<!DOCTYPE html>
<html lang="en">
  
<head>
    <div>
    </div>
    
    </div>
    <meta http-equiv="content-type" 
        content="text/html; charset=UTF-8">
  
    <meta name="viewport" content="width=device-width,
        minimum-scale=1,initial-scale=1">
  
    <script src=
        "https://code.jquery.com/jquery-3.3.1.min.js">
    </script>
  
    <script src=
"https://unpkg.com/jquery.terminal/js/jquery.terminal.min.js">
    </script>
  
    <link rel="stylesheet" href=
"https://unpkg.com/jquery.terminal/css/jquery.terminal.min.css" />
  
    <style type="text/css">
        .terminal,
        span,
        .cmd,
        div {
            --color: rgba(255, 255, 255, 0.99);
        }
  
        .terminal,
        span {
            --size: 1.4;
        }
    </style>
</head>
<style>
    body {
    margin: 0;
    background: rgb(0, 0, 0);
}
.terminal img[src*="blob:"], .terminal video {
    max-width: 100%;
}
#terminal {
    height: 100vh;
}

:root {
    --background: #000000;
}
@media (min-width: 800px) {
    :root {
        --size: 1.2;
    }
}
@media (min-width: 1200px) {
    :root {
        --size: 1.4;
    }
}
/* to see yourself like in a mirror */
.self {
    transform: scale(-1, 1);
}
.flicker {
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    background: rgba(14, 14, 14, 0.2);
    opacity: 0;
    z-index: 1000;
    pointer-events: none;
    animation: flicker 0.12s infinite;
}
@keyframes flicker {
  0% {
    opacity: 0.552;
  }
  5% {
    opacity: 0.48287;
  }
  10% {
    opacity: 0.59134;
  }
  15.0% {
    opacity: 0.79543;
  }
  20% {
    opacity: 0.75134;
  }
  25% {
    opacity: 0.1956;
  }
  30.0% {
    opacity: 0.90687;
  }
  35% {
    opacity: 0.122;
  }
  40% {
    opacity: 0.62254;
  }
  45% {
    opacity: 0.56977;
  }
  50% {
    opacity: 0.9925;
  }
  55.0% {
    opacity: 0.55487;
  }
  60.0% {
    opacity: 0.16607;
  }
  65% {
    opacity: 0.12353;
  }
  70% {
    opacity: 0.2214;
  }
  75% {
    opacity: 0.67908;
  }
  80% {
    opacity: 0.97163;
  }
  85.0% {
    opacity: 0.1275;
  }
  90% {
    opacity: 0.37186;
  }
  95% {
    opacity: 0.24475;
  }
  100% {
    opacity: 0.37221;
  }
}
.scanlines {
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    background: linear-gradient(
        to bottom,
        rgba(255,255,255,0),
        rgba(255,255,255,0) 50%,
        rgba(0,0,0,.2) 70%,
        rgba(0,0,0,.6)
    );
    background-size: 100% .3rem;
    position: fixed;
    pointer-events: none;
}
.scanlines:before {
  position: absolute;
  top: 0px;
  width: 100%;
  height: 5px;
  background: #fff;
  background: linear-gradient(to bottom,
      rgba(255,0,0,0) 0%,
      rgba(255,250,250,1) 50%,
      rgba(255,255,255,0.98) 51%,
      rgba(255,0,0,0) 100%
  ); /* W3C */
  opacity: .1;
}
.scanlines:after {
  box-shadow: 0 2px 6px rgba(25,25,25,0.2),
      inset 0 1px rgba(50,50,50,0.1),
      inset 0 3px rgba(50,50,50,0.05),
      inset 0 3px 8px rgba(64,64,64,0.05),
      inset 0 -5px 10px rgba(25,25,25,0.1);
}
#terminal:focus-within ~ .scanlines:before {
    content: '';
    display: block;
    animation: vline calc(var(--time, 2) * 1s) linear infinite;
}
/*
 * MS Edge don't support focus-within and css vars
 * inside pseudo selector
 */
@supports (-ms-ime-align:auto) {
    .scanlines:before {
        content: '';
        animation: vline 3s linear infinite;
    }
}
@keyframes vline {
  to { transform: translate(0, 100vh)}
}
/* turn off animation */
.tv {
    height: 100vh;
    position: relative;
}
.tv.collapse {
    animation: size 2s ease-out;
    animation-fill-mode: forwards;
}
.tv.collapse:before {
    content: '';
    display: block;
    height: 100%;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    top: 0;
    background: white;
    z-index: 1;
    opacity: 0;
    animation: opacity 2s ease-out;
    animation-fill-mode: forwards;
}

@keyframes opacity {
    to { opacity: 1; }
}
@keyframes size {
    50% {
        transform: scaleX(calc(1 / var(--width)));
        opacity: 1;
    }
    98% {
        transform: scaleX(calc(1 / var(--width))) scaleY(calc(1 / var(--height)));
        opacity: 1;
    }
    100% {
        transform: scaleX(calc(1 / var(--width))) scaleY(calc(1 / var(--height)));
        opacity: 0;
    }  
}
#terminal {
    padding-bottom: 36px;
}
.collection {
    position: absolute;
    bottom: 0;
    left: 0;
    padding: 10px;
}
.noise {
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    z-index: 2000;
    opacity: 0.05;
    pointer-events: none;
    background: 
        repeating-radial-gradient(#000 0 0.0001%,#fff 0 0.0002%) 50% 0/2500px 2500px,
        repeating-conic-gradient(#000 0 0.0001%,#fff 0 0.0002%) 50% 50%/2500px 2500px;
    background-blend-mode: difference;
    animation: shift .2s infinite alternate;
}
@keyframes shift {
    100% {
        background-position: 50% 0, 50% 60%;
    }
}
@media (prefers-reduced-motion) {
    .noise, .flicker, .scanlines:before {
        animation: none !important;
    }
}
</style>

  
<body>
    
    <script>
        $('body').terminal({
            iam: function (name) {
                this.echo('Hello, ' + name +
                    '. Welcome to GeeksForGeeks');
            },
            founder: function () {
                this.echo('Sandeep Jain');
            },
            help: function () {
                this.echo('\n'
                + '\n'
                + '\n'
                + '*-------------[List of Commands]-------------*'
                + '\n'
                + '\n'
                + 'gallery: [view image gallery]'
                + '\n'
                + '\n'
                + 'x1maginary: [x]'
                + '\n'
                + '\n'
                + 'kbot: [???]'
                + '\n'
                + '\n'
                + 'mp: [v13w023918]'
                + '\n'
                + '\n'
                + 'pnx: [f1ndph33n1x]'
                + '\n'
                + '\n'
                + 'arxie: [0]'
                + '\n'
                + '\n'
                + 'wrld: [takeatrip]'
                + '\n'
                + '\n'
                + ''
                + '\n'
                + '\n'
                + 'home: [g044444b444ck44444]'
                + '\n'
                + '\n'
                + 'clear: [clear terminal screen]'
                + '\n'
                + '\n'
                );
                
            },
            x1maginary: function () {
                this.echo('thiswillpopupifutypetheimaginarycommand'
                + '\n'
                + 'x000x000x000x000x');
                
            },
            gallery: function () {
                this.echo('\n'
                + '\n'
                + '          [X//winter/2012*//<-3]'
                + '\n'
                + '\n'
                )
                this.echo($('<img src="https://i.imgur.com/awqIVSc.jpg">'));
                this.echo('\n'
                + '\n'
                + 'test'
                + '\n');
                this.echo($('<img src="https://i.imgur.com/AsD4R7c.jpg">'))
                
            },
            go_home: function () {
                this.echo('thiswillpopupifutypetheimaginarycommand'
                + '\n'
                + 'founder to know the founder');
                
            },
            magazine: function () {
                this.echo('thiswillpopupifutypetheimaginarycommand'
                + '\n'
                + 'founder to know the founder');
                
            },
            kbot: function () {
                this.echo('thiswillpopupifutypetheimaginarycommand'
                + '\n'
                + 'founder to know the founder');
                
            },
            pnx: function () {
                this.echo('thiswillpopupifutypetheimaginarycommand'
                + '\n'
                + 'founder to know the founder');
                
            },
            wrld: function () {
                this.echo('thiswillpopupifutypetheimaginarycommand'
                + '\n'
                + 'founder to know the founder');
                
            },
            mp: function () {
                this.echo('thiswillpopupifutypetheimaginarycommand'
                + '\n'
                + 'founder to know the founder');
                
            },
            wrld: function () {
                this.echo('thiswillpopupifutypetheimaginarycommand'
                + '\n'
                + 'founder to know the founder');
                
            },
            wrld: function () {
                this.echo('thiswillpopupifutypetheimaginarycommand'
                + '\n'
                + 'founder to know the founder');
                
            },
            arxie: function () {
                this.echo($('<img src="https://i.imgur.com/Ydr0ztb.jpg">'));
                this.echo('\n'
                + '[42284 304234--42348029348?]'
                + '\n'
                + '\n'
                );
                
                
            },
        }, {
            greetings: ''
                + '"help" for list of commands'
        });

        
    </script>
    <script>
        var scanlines = $('.scanlines');
var tv = $('.tv');
function exit() {
    $('.tv').addClass('collapse');
    term.disable();
}

// ref: https://stackoverflow.com/q/67322922/387194
var __EVAL = (s) => eval(`void (__EVAL = ${__EVAL}); ${s}`);

var term = $('#terminal').terminal(function(command, term) {
    var cmd = $.terminal.parse_command(command);
    if (cmd.name === 'exit') {
        exit();
    } else if (cmd.name === 'echo') {
        term.echo(cmd.rest);
    } else if (command !== '') {
        try {
            var result = __EVAL(command);
            if (result && result instanceof $.fn.init) {
                term.echo('<#jQuery>');
            } else if (result && typeof result === 'object') {
                tree(result);
            } else if (result !== undefined) {
                term.echo(new String(result));
            }
        } catch(e) {
            term.error(new String(e));
        }
    }
}, {
    name: 'js_demo',
    onResize: set_size,
    exit: false,
    // detect iframe codepen preview
    enabled: $('body').attr('onload') === undefined,
    onInit: function() {
        set_size();
        this.echo('Type [[b;#fff;]exit] to see turn off animation.');
        this.echo('Type and execute [[b;#fff;]grab()] function to get the scre' +
                  'enshot from your camera');
        this.echo('Type [[b;#fff;]camera()] to get video and [[b;#fff;]pause()]/[[b;#fff;]play()] to stop/play');
    },
    onClear: function() {
        console.log(this.find('video').length);
        this.find('video').map(function() {
            console.log(this.src);
            return this.src;
        });
    },
    prompt: 'js> '
});
// for codepen preview
if (!term.enabled()) {
    term.find('.cursor').addClass('blink');
}
function set_size() {
    // for window height of 170 it should be 2s
    var height = $(window).height();
    var width = $(window).width()
    var time = (height * 2) / 170;
    scanlines[0].style.setProperty("--time", time);
    tv[0].style.setProperty("--width", width);
    tv[0].style.setProperty("--height", height);
}

function tree(obj) {
    term.echo(treeify.asTree(obj, true, true));
}
var constraints = {
    audio: false,
    video: {
        width: { ideal: 1280 },
        height: { ideal: 1024 },
        facingMode: "environment"
    }
};
var acceptStream = (function() {
    return 'srcObject' in document.createElement('video');
})();
function camera() {
    if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
        term.pause();
        var media = navigator.mediaDevices.getUserMedia(constraints);
        media.then(function(mediaStream) {
            term.resume();
            var stream;
            if (!acceptStream) {
                stream = window.URL.createObjectURL(mediaStream);
            } else {
                stream = mediaStream;
            }
            term.echo('<video data-play="true" class="self"></video>', {
                raw: true,
                onClear: function() {
                    if (!acceptStream) {
                        URL.revokeObjectURL(stream);
                    }
                    mediaStream.getTracks().forEach(track => track.stop());
                },
                finalize: function(div) {
                    var video = div.find('video');
                    if (!video.length) {
                        return;
                    }
                    if (acceptStream) {
                        video[0].srcObject = stream;
                    } else {
                        video[0].src = stream;
                    }
                    if (video.data('play')) {
                        video[0].play();
                    }
                }
            });
        });
    }
}
var play = function() {
    var video = term.find('video').slice(-1);
    if (video.length) {
        video[0].play();
    }
}
function pause() {
    term.find('video').each(function() {
        this.pause(); 
    });
}

function grab() {
    if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
        term.pause();
        var media = navigator.mediaDevices.getUserMedia(constraints);
        media.then(function(mediaStream) {
            const mediaStreamTrack = mediaStream.getVideoTracks()[0];
            const imageCapture = new ImageCapture(mediaStreamTrack);
            return imageCapture.takePhoto();
        }).then(function(blob) {
            term.echo('<img src="' + URL.createObjectURL(blob) + '" class="self"/>', {
                raw: true,
                finialize: function(div) {
                    div.find('img').on('load', function() {
                        URL.revokeObjectURL(this.src);
                    });
                }
            }).resume();
        }).catch(function(error) {
            term.error('Device Media Error: ' + error);
        });
    }
}
async function pictuteInPicture() {
    var [video] = $('video');
    try {
        if (video) {
            if (video !== document.pictureInPictureElement) {
                await video.requestPictureInPicture();
            } else {
                await document.exitPictureInPicture();
            }
        }
  } catch(error) {
      term.error(error);
  }
}
function clear() {
    term.clear();
}

github('jcubic/jquery.terminal');
cssVars(); // ponyfill






    </script>

</body>
  
</html>
