---
title: "usopen.org Live stream shows-up in inverted color scheme"
date: 2012-09-04
forum: General Help
---

### Post by sazhagianambi on 2012-09-04
Hi, 

I been using Ubuntu 12.04 on Sony Vaio F11 machine. I see a Weird issue and like to verify as some body else see the same issue, ot its something really wrong in mine. 

since my laptop uses the NVIDIA 330M card, with fresh installation external monitor didn't get supported. So I removed the open NVDIA drivers installed and installed the official NVDIA drivers. Now both external monitor to TV and HDMI sound works...

However when I try to watch Live stream from USOPEN.ORG all blue colors are inverted and shows up in purple color including the tennis court(picture in picture looks in normal colors)....  Espn3.com seems fine though, all photos looks good...I tried Firefox, chromium both with same result...

usopen.org video seems fine in WIndows 8/Mac machine..

Did anybody in US watched the live stream using 12.04 machine? did all looked good? Any idea as what could be my issue.  

sorry if its stupid question...

Thank you...

---

### Post by mc4man on 2012-09-04
You need a patched libvdpau1
12.10 now has it by default
You could either install the 12.10 libvdpau1 package or add this ppa, update your sources & then update libvdpau1

[https://launchpad.net/~tikhonov/+archive/misc?field.series_filter=precise](https://launchpad.net/~tikhonov/+archive/misc?field.series_filter=precise)

```
sudo add-apt-repository ppa:tikhonov/misc
```
ect.

---

### Post by sazhagianambi on 2012-09-04
Thank you mc4man.....I added that and installed the libvdpau1..the restart system resolved like charm...

just curious as what would be cause and how this package solved the issue...

Thanks again.

-Nambi

---

### Post by mc4man on 2012-09-04
The issue was a bug in adobe flash that isn't going to be fixed in flash.
I guess the 1st. answer here can give you some idea of the issue & shows some of the workarounds.
Ultimately the best solution was to patch libvdpau which made it into the 12.10 versions but not 12.04, ect. So the ppa picked up the slack.

[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)
some specifics
[http://lists.freedesktop.org/archives/vdpau/2012-May/000022.html](http://lists.freedesktop.org/archives/vdpau/2012-May/000022.html)

---

### Post by sazhagianambi on 2012-09-05
Thank you very much for the help and details..

---

