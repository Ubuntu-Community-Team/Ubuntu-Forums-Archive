---
title: "Play and pause buttons in youtube do not work."
date: 2009-11-03
forum: General Help
---

### Post by bhishan on 2009-11-03
The play and pause button in youtube videos do not work in Karmic. They used to work for a couple of days after I installed Karmic, and stopped working all of a sudden. Anyone have any idea?

---

### Post by Jugney on 2009-11-04
I am seeing this as well, but only in Chrome (Linux version). Firefox works fine.

---

### Post by viniciuscarvalho on 2009-11-04
This is a BUG, and its not only youtube. Eclipse is not working properly as well. It only happens if you have compiz enabled. I'm thinking going back to 9.04 because of this...

---

### Post by 55tptag on 2009-11-04
Same problem here when using Ubuntu 64-bit.  Using Ubuntu 32-bit youtube works better.

---

### Post by bhishan on 2009-11-04
> **viniciuscarvalho said:**
> This is a BUG, and its not only youtube. Eclipse is not working properly as well. It only happens if you have compiz enabled. I'm thinking going back to 9.04 because of this...

By compiz enabled, do you mean system>preferences>appearance>visual effects>extra   ?

---

### Post by ea1387 on 2009-11-04
My buttons in youtube wasnt working either.A new update today must have fixed it because i just disabled compiz, went to youtube played with the buttons and then turned compiz back on and the problem is not there anymore.

---

### Post by kelvin.illa on 2009-11-05
There's an easy fix to this; it can be found in this forum but I show it here anyway.

As have been said before, the problem is with the 64-bit version of flash. So, first of all, uninstall your currently installed flash (via Software Center, Synaptic, or Terminal).

Download the 64-bit version 10 from the website: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Put the 'libflashplayer.so' file to /usr/lib/mozilla/plugins. You might need root privileges (but I'm not sure); if you do, just run Terminal and type "sudo nautilus." This will open up the file manager as root user. 

Restart firefox.

---

### Post by bhishan on 2009-11-05
> **kelvin.illa said:**
> There's an easy fix to this; it can be found in this forum but I show it here anyway.

As have been said before, the problem is with the 64-bit version of flash. So, first of all, uninstall your currently installed flash (via Software Center, Synaptic, or Terminal).

Download the 64-bit version 10 from the website: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Put the 'libflashplayer.so' file to /usr/lib/mozilla/plugins. You might need root privileges (but I'm not sure); if you do, just run Terminal and type "sudo nautilus." This will open up the file manager as root user. 

Restart firefox.

I am currently in my office. I will try it when I return home and post the result. Thanks.

---

### Post by 55tptag on 2009-11-05
> **kelvin.illa said:**
> There's an easy fix to this; it can be found in this forum but I show it here anyway.

As have been said before, the problem is with the 64-bit version of flash. So, first of all, uninstall your currently installed flash (via Software Center, Synaptic, or Terminal).

Download the 64-bit version 10 from the website: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Put the 'libflashplayer.so' file to /usr/lib/mozilla/plugins. You might need root privileges (but I'm not sure); if you do, just run Terminal and type "sudo nautilus." This will open up the file manager as root user. 

Restart firefox.

FYI: apparently that workaround doesn't work for everyone. I tried it during my 64-bit heydays and youtubes "play and pause buttons in youtube do not work".  Thanks.  But, sorry it's not the fix for everyone.

---

### Post by brianfactors on 2009-11-08
Same problem here. I actually went through a phase were flash completely didn't work. Then I enabled a few of the repos that got turned off during update and got it back.

I am running a 64 bit version of Karmac.

This is really weird. Here are the specific problems:
-works with Dailymotion, Tangle, Vimeo, etc.
-does NOT work with Youtube or Facebook videos.
These are all the players I've tested it with.

Apparently it is only a firefox & flash issue. Youtube performs seamlessly on Opera.

Now I'm wondering if part of it could be a java issue... Youtube uses Java for some stuff, right?

I'm not quite sure were the problem is, so I don't know how to file a bug on this one... I've run FF from the prompt, and I didn't see anything fishy. :-k

Update: Really strange... this guy says that the problem was Compiz: [http://ubuntuforums.org/showthread.php?t=1318746](http://ubuntuforums.org/showthread.php?t=1318746)
That doesn't make very much sense to me...
More: [http://ubuntuforums.org/showthread.php?t=1293921](http://ubuntuforums.org/showthread.php?t=1293921)

Update 2: Apparently the problem is linked to Compiz. Running "metacity --replace" (with alt + F2), which stops my cool compiz effects makes youtube work just fine. What that is, I haven't the first clue...

---

### Post by DynastyX on 2009-11-08
From what I gather from this, it can't be fixed. I tried the above solution a while ago but it made firefox crash whenever I viewed a flash enabled website. My solution was to use the 32 bit Karmic instead.

---

### Post by brianfactors on 2009-11-09
Like I said, it's not beyond repair. Appears that disabling compiz (ie: by running "metacity --replace" or completely disabling visual effects) solves it (at least temporarily).

Still don't get how compiz has anything to do with plugins INSIDE of Firefox. Like I said, Opera was just fine.

---

### Post by bhishan on 2009-11-09
I hope this issue gets solved fast. I had the same annoying in Jaunty for six months. It is a little better in Karmic. If it gets fixed, then only it will be a real competitor for Windows and OSX. All the trouble it gives me, I will still stick with it, hoping for the best.

---

### Post by 55tptag on 2009-11-10
> **bhishan said:**
> I hope this issue gets solved fast.
Don't hold your breath.

---

### Post by brianfactors on 2009-11-12
Ok, why did this thread get marked "SOLVED." Disabling Compiz just so that you can get flash to work INSIDE of Firefox is not what I call a FIX.

Compiz should not mess with flash in Firefox. It doesn't in Opera.

This is still a bug, and it is not fixed. I think this is the official bug on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

Then again, we should move this to another thread... maybe? If that's why it's marked, then sorry to waste your time. I'm still getting used to how the forum works...

---

### Post by bhishan on 2009-11-12
> **brianfactors said:**
> Ok, why did this thread get marked "SOLVED." Disabling Compiz just so that you can get flash to work INSIDE of Firefox is not what I call a FIX.

Compiz should not mess with flash in Firefox. It doesn't in Opera.

This is still a bug, and it is not fixed. I think this is the official bug on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

Then again, we should move this to another thread... maybe? If that's why it's marked, then sorry to waste your time. I'm still getting used to how the forum works...

I marked it solved coz it has been recognized as a bug of high priority in the launchpad. I thought that there is no use posting in this forum if the developers are working on it. It would have been better if we could mark forums [fix in progress] or something like that.

---

### Post by brianfactors on 2009-11-14
Ah, gotcha. Makes sense now. I hope the launchpad gurus have it all under control... In fact, I know they do.

---

### Post by OwnSurname on 2009-11-15
Same problem here, but with Opera as well. Running Ubuntu 9.10 64-bits, Opera 10.01 Build 4682. I have the 64-bits version of Flash Player installed too. I can't use Youtube buttons if Compiz effects are on normal, while everything work perfectly if none. This problem is recent, days ago everything was working fine for me with normal effects, and never had such a problem with 9.04. I still wonder how can you break something that works perfectly before.

---

### Post by synec on 2009-12-16
I have the general problem of Flash buttons not working. This manifests itself with both Youtube and Pandora.

The problem is the same for Firefox, Chrome, and Opera.

Setting visual effects to "None" in Compiz causes the problem to go away temporarily. Eventually the problem returns.

Curiously, I sometimes get a successful Flash button press in when one of the browsers first starts, but never afterward.

I'm running 64 bit 9.10 updated to the latest as of this writing. I'm also using Nvidia's proprietary drivers, version 185.

---

### Post by ruario on 2009-12-19
Google gdk_native_windows and it will all make sense. Affected Opera users can use [this workaround]("http://my.opera.com/ruario/blog/flash-problems-on-linux#first-click").

---

### Post by alambpencil on 2010-06-23
The solution for me in Ubuntu 10.04 64 was:
 

$sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
 ----ORIGINAL------
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
. /usr/lib/nspluginwrapper/noarch/npviewer
-----------------------
 -----EDITED--------
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
-----------------------
 Save, and restart firefox, buttons now work!

---

### Post by Paddy Landau on 2010-06-25
> **alambpencil said:**
> sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
...
export GDK_NATIVE_WINDOWS=1
Thanks! It solved the problem for me.

I think that the bug should be re-opened.

By the way, for GUI programs, please use **gksu** instead of **sudo** (if you run the program with Alt-F2, as I did, the reason will become apparent).

---

### Post by lariosa42 on 2010-07-12
alambpencil's solution worked for me.  

I'm running 64-bit Lucid (10.04), firefox version 3.6.6.  I didn't have to reinstall flash or anything (as suggested in previous posts).

---

### Post by naveenroy on 2010-07-29
Wow, cool - alambpencil's solution worked great and I am running the 64-bit edition of 10.04 too. Thanks for that!

[www.naveenroy.com](www.naveenroy.com)
[www.un-clicked.com](www.un-clicked.com)

---

### Post by tkrisz on 2010-07-29
Thx, solved my problem, too.

---

### Post by atscott01 on 2010-09-07
> **alambpencil said:**
> The solution for me in Ubuntu 10.04 64 was:
 

$sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
 ----ORIGINAL------
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
. /usr/lib/nspluginwrapper/noarch/npviewer
-----------------------
 -----EDITED--------
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
-----------------------
 Save, and restart firefox, buttons now work!

Yay!

---

### Post by bmach on 2010-09-12
> **alambpencil said:**
> The solution for me in Ubuntu 10.04 64 was:
 

$sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
 ----ORIGINAL------
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
. /usr/lib/nspluginwrapper/noarch/npviewer
-----------------------
 -----EDITED--------
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
-----------------------
 Save, and restart firefox, buttons now work!

worked for me! many thanks. This was really annoying me. :popcorn:

---

