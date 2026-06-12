---
title: "Skype and googletalk-plugin crashing when I start webcam"
date: 2011-01-10
forum: General Help
---

### Post by Mauri72 on 2011-01-10
Hi all,
I have a Vaio laptop with Ubuntu 10.10 64 bit and until about 2 or 3 weeks ago Skype and google talk video chat were working perfectly. I have been away for a break and today I tried to use Skype , which I usually laungh using the sky-wrapper file which is:```
#!/bin/sh

if [ ! -e ~/.Skype/shared.xml ]; then
  mkdir -p ~/.Skype
  cp /usr/share/skype/shared.xml ~/.Skype/shared.xml
fi

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so QT_PLUGIN_PATH=/usr/lib32/qt4/plugins /usr/bin/skype "$@"

```Well every time I tried to start the webcam, Skype crashed (with a segmentation fault). This happens also in the Option screen when I press "Test"
I tried to launch it simply with /usr/bin/skype and it looks like the cam works that way, as the person I was talking to seemed able to see me, but no image from my cam was shown on my screen.
I went onto google then to use google talk and again when I tried to start the cam Firefox crashed.
I started up Cheese and there the cam is working perfectly. 
Very strange because as I said both Skype and google talk plugin were working just fine until recently. Has anyone bumped into this and is there any solution?
Cheers
Mauri

---

### Post by Mauri72 on 2011-01-11
Am I really the only one experiencing this? wow that's bad luck eheheh

---

### Post by banyai on 2011-01-29
I have Ubuntun 10.10 64 bit  with a Logitech C500 Webcam and Skype crashes immediately as I start video. 
Regards,
banyai

---

### Post by pwabrahams on 2011-02-06
This says it all:```
pwa@Asus-laptop:~$ LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so /usr/bin/skype
Segmentation fault
pwa@Asus-laptop:~$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype
Segmentation fault

```
This happens, of course, with the Skype video test.  And cheese works fine.  Moreover, I have the same result with two different webcams.

To add to my frustrations, the video test worked a few weeks ago, so I've been clobbered by one of the updates.  I'm running Kubuntu 10.10.

---

### Post by banyai on 2011-04-13
> **banyai said:**
> I have Ubuntun 10.10 64 bit  with a Logitech C500 Webcam and Skype crashes immediately as I start video. 
Regards,
banyai

):P With the last Ubuntu update (april 2011) the problem was solved!

---

