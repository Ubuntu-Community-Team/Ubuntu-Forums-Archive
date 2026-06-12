---
title: "Firefox shuts down randomly"
date: 2011-09-24
forum: General Help
---

### Post by Flying Mandarine on 2011-09-24
Hello everyone,

Firefox shuts down rather randomly, the average being every thirty minutes, but it can also stay stable for a few hours, or shut down after just five minutes.

It has been doing that for only about a week, maybe less. I've reinstalled the Adobe Flash Player but it didn't change anything. Curiously, it looks like it crashes more often when on websites that use Flash, such as Grooveshark.com, but I'm not so sure.

Here's the output I get from a typical crash:

```

"Add-ons: {59c81df5-4b7a-477b-912d-4e0fdf64e5f2}:0.9.87,tineye@ideeinc.com:1.1,{DDC359D1-844A-42a7-9AA1-88A850A938A8}:2.0.7,ubufox@ubuntu.com:0.9.1,langpack-ja@firefox.mozilla.org:6.0.2,langpack-en-GB@firefox.mozilla.org:6.0.2,langpack-fr@firefox.mozilla.org:6.0.2,globalmenu@ubuntu.com:1.0.7,langpack-en-ZA@firefox.mozilla.org:6.0.2,{972ce4c6-7e08-4474-a285-3208198ce6fd}:6.0.2
BuildID: 20110905174115
CrashTime: 1316867221
EMCheckCompatibility: true
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1315375202
Notes: OpenGL: ATI Technologies Inc. -- ATI Radeon HD 5800 Series  -- 4.1.10665 Compatibility Profile Context
WebGL? libGL.so.1? libGL.so.1+
GL Context? GL Context+
WebGL+

ProductName: Firefox
ReleaseChannel: release
SecondsSinceLastCrash: 335
StartupTime: 1316866933
Theme: classic/1.0
Throttleable: 1
URL: wyciwyg://13/http://www.okcupid.com/home?cf=logo
Vendor: Mozilla
Version: 6.0.2

```

This report also contains technical information about the state of the application when it crashed."


It has never done that before, not even once, to my knowledge. I don't remember having done anything these last days that could cause that, except updating Ubuntu 11.04 like I do every morning. I don't know if it has any importance, but twice during the last two months, there was a problem on the update concerning a certain VirtualBox (if I recall correctly).

I have searched in the forum for similar threads, but those I've found are a bit old, so I'm a little scared to try to mess around with Ubuntu since it's changed quite a lot in the last years.

Thanks in advance!

---

### Post by dino99 on 2011-09-24
which ubuntu are you using, is it genuine packages or from ppa ? is it a standard installation (not inside wubi or virtualbox or else ) ?

look at free partition space inside system monitor

```
sudo dpkg-reconfigure -phigh -a
```

( can take a while, dont stop it)

standard install:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Flying Mandarine on 2011-09-24
Thanks for the quick answer, dino99!

Unfortunately, I cannot change my details on the left (not enough posts) so it says 9.10 when I actually use Ubuntu 11.04. As far as packages go, I... suppose they are genuine, yes; I didn't mess up with the repositories and the packages much, I think? It is a standard installation.

I looked inside the system monitor but I'm not sure I follow you when you speak of free partition space. If you mean, free space on the computer on the partition I'm using, then yes, more than 100 gb.

I launched that command in the terminal, there were a few errors from time to time (some pertaining to VirtualBox). My FireFox hasn't crashed yet, but I will repost if it does.

I read your link, but I'm not sure what to do with it. Do you mean I need to reinstall Ubuntu if the problem is still there?

---

### Post by dino99 on 2011-09-24
from "system monitor" i was speaking of the last tab (4th) showing % used of / & /home: need at least 10 % free to run smootly

mabe you can find usefull errors logged into:
/var/log/
.xsession-errors (into /home, ctrl+h to unhide it)

look also at /var/crash/ and report if you had one (double click on it).

if you close firefox and the other opened apps and then run firefox from a terminal, did you get errors/warnings ?

sudo firefox

---

### Post by Flying Mandarine on 2011-09-24
"/dev/sda5" is 34% free, more than a hundred Gb; there are no other devices though.

It still hasn't crashed yet, so if it does so, I will run FireFox from the terminal and paste the output after the next crash. In the meantime, fingers crossed!

---

### Post by dino99 on 2011-09-24
i'm happy for you, this kind of issue is often due to site(s) using "flash" but with bad config/settings, so you cant do much about that sadly, thinks to use FF addons for security (plugins)

---

### Post by SecretCode on 2011-09-24
I suspect an issue with flash itself, though it could be other things.

Are you running 32 bit Ubuntu or 64 bit? ```
uname -m
``` will tell you

And what version of Flash do you have? In Firefox, Add-ons > Plugins will tell you - mine is "Shockwave Flash 11.0 r1"

```
aptitude search flashplugin
```
will show which flash plugin package you have.

---

### Post by Flying Mandarine on 2011-09-25
dino99:

Unfortunately, the problem is still there; there is no output on the terminal at the moment of the crash, but pretty often (say, every five minutes), this error appears: 

> Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory


I quickly searched the Internet for that error; I read that I should switch the video output of mplayer from VDPAU to something else, but it wasn't VDPAU in the first place (x11 I think), when I opened mplayer. Maybe something else (or a FireFox plugin of mplayer) uses VDPAU?

And, from time to time only, these two messages appear too:

> Can't find symbol 'glXBindTexImageEXT'
Can't find symbol 'glXReleaseTexImageEXT'



SecretCode:

I think I'm running 32 bit. When I run uname -m, it only says 'i686.' As for Flash, FireFox indicates I'm running Shockwave Flash 10.3 r183 (curiously, an earlier version than yours, although I keep everything up to date; but maybe it already was up to date before I uninstalled and reinstalled it, I wouldn't know).

As for aptitude search flashplugin:

> p   adobe-flashplugin               - Adobe Flash Player plugin version 10      
i   flashplugin-installer           - Adobe Flash Player plugin installer       
p   flashplugin-nonfree             - Adobe Flash Player plugin installer (trans
p   flashplugin-nonfree-extrasound  - Adobe Flash Player platform support librar


Thanks for the help, past and future

---

### Post by Flying Mandarine on 2011-09-25
Oh, I should probably add that I had a nVidia card (GeForce 9600) which I recently replaced with an ATi Radeon 5850. It was about three months ago and that FireFox shutdown problem only began about ten days ago, so I wouldn't think it's related, but you never know, what with that nVidia VDPAU error. I removed the nVidia driver, as far as I remember, before replacing it with the ATi one.

---

### Post by SecretCode on 2011-09-25
If you were running 64bit Ubuntu I would have recommended moving to 64bit flash ... but that's not applicable.

Another idea: [create a new test profile]("http://support.mozilla.com/en-US/kb/Managing-profiles") in Firefox and see if it occurs using that profile. Install any extensions you use one by one to see if they are the cause.

---

### Post by Flying Mandarine on 2011-09-25
Alright, will do. It looks like it's crashing less often, but it still does, so it's going to take a long time to install these extensions one by one and see if the crash still happens.

I will report once that's done!

---

### Post by lovinglinux on 2011-09-26
Firefox normally should not crash because of flash, since it has plugin process separation. Usually, it will crash only the flash content.

Please try [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/") extension to avoid loading unnecessary flash content.

Also try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/), to improve flash performance and fix common issues. If you r card supports VDPAU, then Flash-Aid will make the necessary changes to use it.

---

