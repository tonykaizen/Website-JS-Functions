function convertVttToJson(vttString) {
    return new Promise((resolve, reject) => {
        var current = {}
        var sections = []
        var start = false;
        var vttArray = vttString.split('\n');
        vttArray.forEach((line, index) => {
            if (line.replace(/<\/?[^>]+(>|$)/g, "") === " ") {
            } else if (line.replace(/<\/?[^>]+(>|$)/g, "") == "") {
            } else if (line.indexOf('-->') !== -1) {
                start = true;

                if (current.start) {
                    sections.push(clone(current))
                }

                current = {
                    start: timeString2ms(line.split("-->")[0].trimRight().split(" ").pop()),
                    end: timeString2ms(line.split("-->")[1].trimLeft().split(" ").shift()),
                    part: ''
                }
            } else if (line.replace(/<\/?[^>]+(>|$)/g, "") === "") {
            } else if (line.replace(/<\/?[^>]+(>|$)/g, "") === " ") {
            } else {
                if (start) {
                    if (sections.length !== 0) {
                        if (sections[sections.length - 1].part.replace(/<\/?[^>]+(>|$)/g, "") === line.replace(/<\/?[^>]+(>|$)/g, "")) {
                        } else {
                            if (current.part.length === 0) {
                                current.part = line
                            } else {
                                current.part = `${current.part} ${line}`
                            }
                            // If it's the last line of the subtitles
                            if (index === vttArray.length - 1) {
                                sections.push(clone(current))
                            }
                        }
                    } else {
                        current.part = line
                        sections.push(clone(current))
                        current.part = ''
                    }
                }
            }
        })

        current = []

        sections.forEach(section => {
            section.part = section.part.replace(/<\/?[^>]+(>|$)/g, "")
        })
        resolve(sections);
    })
}

// helpers
//   http://codereview.stackexchange.com/questions/45335/milliseconds-to-time-string-time-string-to-milliseconds
function timeString2ms(a, b) {// time(HH:MM:SS.mss) // optimized
    return a = a.split('.'), // optimized
        b = a[1] * 1 || 0, // optimized
        a = a[0].split(':'),
        b + (a[2] ? a[0] * 3600 + a[1] * 60 + a[2] * 1 : a[1] ? a[0] * 60 + a[1] * 1 : a[0] * 1) * 1e3 // optimized
}

function clone(obj) {
    if (null == obj || "object" != typeof obj) return obj;
    var copy = obj.constructor();
    for (var attr in obj) {
        if (obj.hasOwnProperty(attr)) copy[attr] = obj[attr];
    }
    return copy;
}

document.addEventListener('DOMContentLoaded', () => {       
  var audioSync = function (options) {
        const controls = [
            'play-large', // The large play button in the center
            'rewind', // Rewind by the seek time (default 10 seconds)
            'play', // Play/pause playback
            'fast-forward', // Fast forward by the seek time (default 10 seconds)
            'progress', // The progress bar and scrubber for playback and buffering
            'current-time', // The current time of playback
            'duration', // The full duration of the media
            'captions', // Toggle captions
            'settings', // Settings menu
            'airplay', // Airplay (currently Safari only)
            'download', // Show a download button with a link to either the current source or a custom URL you specify in your options
        ];

        const player = new Plyr('#player', { controls });

        player.source = {
            type: 'audio',
            sources: [
                {
                    src: '{{wf {&quot;path&quot;:&quot;audio-file&quot;,&quot;type&quot;:&quot;PlainText&quot;\} }}',
                    type: 'audio/mp3',
                }
            ],
        };

                var $subtitles = $('#subtitles-container');
        var $membershipRequired = $('subtitles-container-private');

        $.get('{{wf {&quot;path&quot;:&quot;transcript-file&quot;,&quot;type&quot;:&quot;PlainText&quot;\} }}', function (data) {
            convertVttToJson(data)
                .then((result) => {
                    player.on('timeupdate', function ({ timeStamp }) {
                        if (options.isMember === false && player.currentTime > free_seconds) {
                            $membershipRequired.show();
                            $subtitles.hide();
                            return;
                        }
                        else {
                            $membershipRequired.hide();
                            $subtitles.show();
                        }
                        const currentTimeMs = player.currentTime * 1000;
                        console.log(currentTimeMs);
                        const match = result.find(a => a.start <= currentTimeMs && a.end >= currentTimeMs);
                        if (match) {
                            $('#subtitles').text(match.part);
                        } else {
                            $('#subtitles').text('');
                        }
                    })
                });
        })
    }

    MemberStack.onReady.then(function (member) {
        var _isMember = false;
        if (member.membership && member.membership.status === "active") {
            _isMember = true;
        }

        audioSync({
            isMember: _isMember
        });
    })
})
