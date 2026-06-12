---
title: "webcamera setting"
date: 2009-11-25
forum: General Help
---

### Post by wierdlmate on 2009-11-25
When I try to use my logitech quickam messenger, I get a permission problem:

xawtv -c /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.31-15-generic)
xinerama 0: 1680x1050+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Engedély megtagadva
v4l2: open /dev/video0: Engedély megtagadva
v4l: open /dev/video0: Engedély megtagadva
no video grabber device available

(Permission denied)

On the other hand, it is all fine, if I do

sudo xawtv -c /dev/video0

The permissions on /dev/video0 are

$ ls -l /dev/video0
crw-rw----+ 1 root video 81, 0 2009-11-25 13:45 /dev/video0

also

$ grep video /etc/group
video:x:44:dori,marci,apu

---

