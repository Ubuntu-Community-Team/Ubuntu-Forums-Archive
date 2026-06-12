---
title: "Anyone have Flash problems?"
date: 2012-03-15
forum: General Help
---

### Post by Jerry N on 2012-03-15
I am posting this here to see if anyone else has had the same problem or if I am simply out of my head.  

I am having trouble reading what appears to be a flash video in the latest version of Firefox.  It doesn't work with Firefox 10.x in Windows 7 either.  It works fine with Midori in Ubuntu or Google Chrome in Windows.  

One of the videos is at [COLOR="Red"][/COLOR]    [http://www.boeing.com/Features/2012/03/bds_avms_03_12_12.html]("http://www.boeing.com/Features/2012/03/bds_avms_03_12_12.html") [COLOR="Black"][/COLOR]   but I have had others.  I have reinstalled Adobe Flash, both in Ubuntu and in Windows, without solving the problem.

Jerry

---

### Post by dancapp on 2012-03-15
Same! I'm going crazy. I've tried Flash-Aid, package-manager updates, reverting to old versions of flash manually. And worst of all, it just stopped working with an update a few weeks ago and no other Ubuntu users seem to be having a problem (until now).

I'm using KXStudio (basically Ubuntu with KDE), 64 bit. Browsers are Chromium and Firefox and flash is crashing consistently in both. I'm not an advanced Linux user so unless I can find a clear step-by-step guide to get it working I'm lost! :confused:

---

### Post by dragonfly41 on 2012-03-15
I can view it .. ubuntu 10.10 32 bit .. although the video is a bit "choppy" .. have you tried firefox Flash-Aid?

[EDIT]

there is a debugger version of firefox plugin here ..

[http://helpx.adobe.com/flash-player/kb/configure-debugger-version-flash-player.html](http://helpx.adobe.com/flash-player/kb/configure-debugger-version-flash-player.html)

---

### Post by dancapp on 2012-03-15
Sorry but I don't even know what a debugger version is, let alone how it would help.

---

### Post by synaptix on 2012-03-15
Working fine here Ubuntu 11.10 x86_64 with Firefox 10.0.2 and Flash 11.2.202.221. No choppiness or tearing either as I've got tear-free enabled (Catalyst).

---

### Post by dancapp on 2012-03-15
Ok after kicking up a fuss I just managed to fix mine. Hope this works for others too:

1) Uninstall "flashplugin-installer"
2) Check your web browser to make sure no flash plugin at all is installed
3) Install "adobe-flashplugin"

Funny how you try all the complicated processes and then it's often the simple one that works.

---

### Post by Jerry N on 2012-03-15
> **dancapp said:**
> Ok after kicking up a fuss I just managed to fix mine. Hope this works for others too:

1) Uninstall "flashplugin-installer"
2) Check your web browser to make sure no flash plugin at all is installed
3) Install "adobe-flashplugin"

Funny how you try all the complicated processes and then it's often the simple one that works.

I will give that a try later this evening.  Thanks!  At least I know I am not alone:p:p

---

### Post by lovinglinux on 2012-03-15
If you are using Flash-Aid, click the extension Help menu then Generate Report and post here.

---

### Post by Luksion Knight on 2012-03-21
I was having similar problems but recently restored flash functionality by removing gnash from my computer. I think a browser (firefox or chrome) had installed it in an attempt to automatically locate plugins. I noticed > (two files) listed under flash in the plugins page.

Just for the record.

---

### Post by lovinglinux on 2012-03-22
> **Luksion Knight said:**
> I was having similar problems but recently restored flash functionality by removing gnash from my computer. I think a browser (firefox or chrome) had installed it in an attempt to automatically locate plugins. I noticed  listed under flash in the plugins page.

Just for the record.

Flash-Aid can take care of such problem, since it removes conflicting plugins, including gnash, lightspark and adobe plugins installed manually, before installing the selected version.

---

### Post by punkybouy on 2012-03-24
Try using Google Chrome or Chrome instead.

---

### Post by Frogs Hair on 2012-03-24
Success with Opera and FF Nightly . I install Flash via Flash Aid .

---

### Post by HotForLinux on 2012-03-24
I have and have had a lot of problems with flash plugins but I can see the video for which you posted the link with Ubuntu Hardy.

---

