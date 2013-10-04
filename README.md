Marionette.TransitionRegion
===========================

Allows for simple and extensible transition support in marionette. 

demo @
http://jsfiddle.net/saqibshakil/4aBW3/8/

or if you need a bigger preview try


http://saqibshakil.github.io
Usage is as follow

    app.addRegions({
        modules: "#top_left",
        security: "#top_right",
        content: {
            selector: "#app_main_content",
            regionType: app.GL.TransitionRegion
        }
    });
    
New transitions can be added by extending from transitionregion and overriding the following functions

    addBaseAnimate: function (view) {
        var styles = {
            "-moz-transition": "margin-left .25s, margin-right .25s",
            "-webkit-transition": "margin-left .25s, margin-right .25s",
            "-o-transition": "margin-left .25s, margin-right .25s",
            "-ms-transition": "margin-left .25s, margin-right .25s",
            "transition": "margin-left .25s, margin-right .25s"
        };
        view.$el.css(styles);
    },
    addTransitionInit: function (view, region) {
        var styles = {
            "margin-left": (region.$el.width() * -1) + "px",
            "margin-right": (region.$el.width() * 1) + "px"
        };
        view.$el.css(styles);
    },
    removeTransitionInit: function (view) {
        var styles = {
            "margin-left": "",
            "margin-right": ""
        };
        view.$el.css(styles);
    },
    addTransitionIn: function (view) {
        var styles = {
            "margin-left": "0px",
            "margin-right": "0px"
        };
        view.$el.css(styles);
    },
    removeTransitionIn: function (view) {
        var styles = {
            "margin-left": "",
            "margin-right": ""
        };
        view.$el.css(styles);
    },
    addTransitionOut: function (view) {
        var styles = {
            "margin-left": (view.$el.parent().width() * 1) + "px",
            "margin-right": (view.$el.parent().width() * -1) + "px"
        };
        view.$el.css(styles);
    },
    removeTransitionOut: function (view) {
        var styles = {
            "margin-left": "",
            "margin-right": ""
        };
        view.$el.css(styles);
    },
