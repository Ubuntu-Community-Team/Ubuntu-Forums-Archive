---
title: "Ubuntu keeps crashing! I think due to flash."
date: 2010-06-16
forum: General Help
---

### Post by Mr Nemo on 2010-06-16
I'm 99% sure that the 64 bit flash plugin I have keeps crashing my system whenever I watch a video online that requires flash. It doesn't happen all the time, but it happens often enough. Is there any way to fix this? This is really the only problem I have on my system and it would nice to remedy this. On that note, I hear there is a new 64 bit flash plugin in the works by adobe for linux. Anyone hear anything about it. Release date? Can anyone help me with my problem, I'm still a little new to Ubuntu.

---

### Post by Mr Nemo on 2010-06-17
bump

---

### Post by lovinglinux on 2010-06-19
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by lovinglinux on 2010-06-27
What is the current status of your situation?

---

### Post by lovinglinux on 2010-06-27
BTW, Adobe dropped the support for the 64bit for now. No info when a new version will be available.

---

### Post by Mr Nemo on 2010-06-28
switched to 32 bit flash. Nothing has really changed. I'm waiting for the new 64 bit release, I suppose that's all I can do. Thanks for your help.

---

### Post by lovinglinux on 2010-06-28
> **Mr Nemo said:**
> switched to 32 bit flash. Nothing has really changed. I'm waiting for the new 64 bit release, I suppose that's all I can do. Thanks for your help.

Have you tried to create a new Firefox profle to see if the problem persists?

Also please provide more info about your flash.Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by Mr Nemo on 2010-06-28
plugin.expose_full_path already set to true

```

**Shockwave Flash**

 File:  /var/lib/flashplugin-installer/npwrapper.libflashplayer.soVersion:   Shockwave Flash 10.1 r53   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes
```

---

### Post by lovinglinux on 2010-06-28
Try these commands:

```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```

Since you are using a 32bit plugin on 64bit system, I recommend the following:

Open npviewer file...

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

...then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```

The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Save the file and restart the browser.

This will fix unresponsive controls and might help with crashing too.

---

### Post by Mr Nemo on 2010-06-28
ill give it a go and get back to you. Again thanks for your help.

**Did what you said. Guess ill go test out flash. If it isn't flash is there anyway to test for other problems?

---

### Post by lovinglinux on 2010-06-29
> **Mr Nemo said:**
> If it isn't flash is there anyway to test for other problems?

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by khelben1979 on 2010-06-29
When I used Firefox 3.6.x flash videos on YouTube had a tendency to crash when the /tmp catalog got filled up, because Firefox chose to store temporary flash files in there.

Restarting the Firefox web browser the /tmp catalog got cleaned up where it started to store these temp flash files again, so you can check this up if you have the same problem over there.

I'm using Firefox 3.7 alfa version so I don't have this problem any more, it seems. :)

---

### Post by Mr Nemo on 2010-06-29
It's my whole system that is crashing, not just firefox or flash.

---

### Post by khelben1979 on 2010-07-02
> **Mr Nemo said:**
> It's my whole system that is crashing, not just firefox or flash.

I see. Have you looked if it could be an overheating issue? Using flash does push the cpu quite a lot, especially if it's not a modern cpu.

---

### Post by idistech on 2010-08-15
[QUOTE=lovinglinux;9521989]Try these commands:

```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```

This has worked for my 10.04/Flash10.1/Dell GX270/Intel crashing on full screen... Previously I could fix the problem with removing hardware acceleration, but with this setting above ( Thanks lovinglinux ) hardware acceleration and full screen mode works for iplayer etc...

G
:popcorn:

---

### Post by Chriske on 2010-12-02
Thank you so much!

This solution:

[INDENT] sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
[/INDENT] 
worked for me.

I've been having this problem for a long time in Firefox, Opera and Chrome on Ubuntu. It has been really annoying. But now it's fixed! 

Ubuntu 10.04
Dell 64-bit

---

