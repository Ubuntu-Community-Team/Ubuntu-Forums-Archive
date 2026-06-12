---
title: "skype webcam crashes when making video call"
date: 2009-12-27
forum: General Help
---

### Post by davidmohammed on 2009-12-27
Anybody got any ideas on what else I can try to allow me to use my webcam with skype (2.1 beta (ubuntu 32bits 8.10+ from skype.com)?

specs - karmic 32bits
Got a phillips 210nc webcam that is recognised by dmesg as

[ 2896.392815] gspca: probing 0471:032d
[ 2896.635137] zc3xx: probe sif 0x0007
[ 2896.639133] zc3xx: probe sensor -> 000f
[ 2896.639139] zc3xx: Find Sensor PAS106
[ 2896.643268] gspca: probe ok

video is correctly displayed when I try
xawtv -c /dev/video0

video is displayed in vlc but the picture is upside down.

1. with skype I can video call and see the otherside but the other side doesn't see me.
If I use the test video option the video is not displayed.
2. If I try
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype the test video option displays video.  However when either myself or the other side calls skype instantly crashes with a segmentation fault.
3. If I try
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype the test video option displays video.  However when either myself or the other side calls skype instantly crashes with a segmentation fault.

I'm at a loss to what else I can try.

---

### Post by davidmohammed on 2009-12-27
OK,
  solved this myself - maybe this will help others

make sure that your skype does not start video automatically.

When making a call or receiving the call change the video size to either double size or full screen i.e. do not leave the default "normal size".  Then choose the option to send your video to the other person.

Hope this helps someone.

---

