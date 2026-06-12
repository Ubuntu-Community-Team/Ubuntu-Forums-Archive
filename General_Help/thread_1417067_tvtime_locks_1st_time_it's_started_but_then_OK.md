---
title: "tvtime locks 1st time it's started but then OK"
date: 2010-02-26
forum: General Help
---

### Post by fragos on 2010-02-26
I been using tvtime for many Ubuntu releases. It has been a very trouble free application other than the random assignment of /dev/video0 between my TV card and webcam. I fixed that long ago with udev rules. Recently my Karmic system self destructed with the help of Google Chrome and a nasty web site. I had to do a new install of Ubuntu to straiten things out. Now after a boot the 1st time I run tvtime it locks up with a black screen and the ap must be killed to terminate. Next and subsequent times tvtime starts up as expected.

Running from the terminal I get:

fragos@Geo:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/fragos/.tvtime/tvtime.xml
videoinput: Can't free frame 0: Invalid argument
videoinput: Can't free frame 1: Invalid argument
videoinput: Can't free frame 2: Invalid argument
videoinput: Can't free frame 3: Invalid argument
videoinput: Can't free frame 0: Invalid argument
videoinput: Can't free frame 1: Invalid argument
videoinput: Can't free frame 2: Invalid argument
videoinput: Can't free frame 3: Invalid argument

(at this point all is locked up)

Any insights or suggestions?

---

