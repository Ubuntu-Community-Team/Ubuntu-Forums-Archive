---
title: "Firefox Swiftfox &amp; Adobe Player error"
date: 2010-07-12
forum: General Help
---

### Post by sandman3838 on 2010-07-12
Hello

I'm using Ubuntu 10.04 (lucid) (x86_64-linux-gnu) and recently I was having an issue creating Web Links on my desktop from Firefox 3.7 and Swiftfox.  That issue was resolved for a while by doing a full removal through Synaptic and removing the Firefox Folders in the Home Directory.  Unfortunately that issue is back.

My other issue is that I am unable to play Adobe Flash Player and I can't seem to be able to un-install it.   I keep getting fails to un-install errors.  (See Screen shot 1)  I was hoping to do a complete purge of Firefox, Swiftfox, and there plug-ins, followed by a re-installation.

Oh, here is another strange item, take a look at Screen shot 2, if I select any of these players is will reply saying that they are already installed?

Again I just want to do a total purge and install of both Firefox3.7 and Swiftfox and get Flash player up and running.  The issue with saving the links to the desktop I'll just live with that one.

Thank you for all your time and help.

---

### Post by sandman3838 on 2010-07-12
Back again.

Here is an update.

Since my original posting on this I did some reading around and I found that using FLASH AID could correct my issue.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

I found a mention of that 
E: Sub-process /usr/bin/dpkg returned an error code (1)
here from another user
[http://ubuntuforums.org/showthread.php?t=1528878&highlight=Firefox+removal](http://ubuntuforums.org/showthread.php?t=1528878&highlight=Firefox+removal)

I tried it and now Firefox 3.7 Flash Player is working there, however Swiftfox 3.6.3 fails to run.  

Suggestions?

---

### Post by sandman3838 on 2010-07-12
Ok me again

I have been out and about.....
I found this, I'm interested in the Swiftfox section.

[http://www.webupd8.org/2009/09/how-to-install-flash-player-10032-right.html](http://www.webupd8.org/2009/09/how-to-install-flash-player-10032-right.html)

*****************

If you are using Swiftfox, also run these command:

CODE:
rm /usr/lib/swiftfox/plugins/libflashplayer.so
CODE:
ln -s /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/swiftfox/plugins/libflashplayer.so

***********************

On another note I have read that for Adobe Flash player to work you need to remove GNASH?
Is this true?  I went a head and removed it through Synaptic.  
However I still have SWFDEC installed should it be removed as well?


What do you think?

---

### Post by lovinglinux on 2010-07-12
> **sandman3838 said:**
> On another note I have read that for Adobe Flash player to work you need to remove GNASH?
Is this true?  I went a head and removed it through Synaptic.  
However I still have SWFDEC installed should it be removed as well?

Yes, you need to remove both, otherwise Firefox might load them instead of the Adobe plugin. FLASH-AID should take care of that too.

> **sandman3838 said:**
> If you are using Swiftfox, also run these command:

CODE:
rm /usr/lib/swiftfox/plugins/libflashplayer.so
CODE:
ln -s /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/swiftfox/plugins/libflashplayer.so


Don't do that. When you install Swiftfox, it creates a plugin folder which is just a symlink to /usr/lib/mozilla/plugins, so all your plugins wll be already there. If you **rm** the symlink you will delete the one in /usr/lib/mozilla/plugins folder and break flash. Besides, if you are using 64bit, that file doesn't even exist.

I haven't been able to play flash in Swiftfox since the latest flash update. I don't know if it was working before, because I only use Swiftfox sporadically, to provide support.

My personal opinion, ditch Swiftfox completely and compile Firefox yourself. It will run just like Swiftfox if you do it right, without all those Swiftfox issues.

I have a tutorial on compiling Firefox that I haven't updated from my old site. I will try to publish it again today and let you know when is online.

---

### Post by sandman3838 on 2010-07-12
Thanks for the info.

I did as you suggested and I removed Swfdec.

My reason I like Swiftfox is because to does seem to be a whole lot faster that Firefox.  That said I have no problem fixing up the Firefox 3.7 or removing both Firefox and Swiftfox and reinstalling to whatever version or method you might suggest?  Even to reinstalling again your flash aid.

Totally your call.

I have to go to my sisters for a bit I'll check back in later tonight.

---

### Post by lovinglinux on 2010-07-12
> **sandman3838 said:**
> Thanks for the info.

I did as you suggested and I removed Swfdec.

My reason I like Swiftfox is because to does seem to be a whole lot faster that Firefox.  That said I have no problem fixing up the Firefox 3.7 or removing both Firefox and Swiftfox and reinstalling to whatever version or method you might suggest?  Even to reinstalling again your flash aid.

Totally your call.

I have to go to my sisters for a bit I'll check back in later tonight.

If you compile it properly, it can run faster than Swiftfox.

The tutorial is ready, but I want to make sure the PGO compilation works. It will take some time to finish. 

Stay tuned.

---

### Post by sandman3838 on 2010-07-12
Not a problem! 
Take as much time as you need.
I'll check my email tomorrow.

Again thanks for all your help.

---

### Post by lovinglinux on 2010-07-12
> **sandman3838 said:**
> Not a problem! 
Take as much time as you need.
I'll check my email tomorrow.

Again thanks for all your help.

It will take more time than expected, since the PGO build is failing.

---

### Post by sandman3838 on 2010-07-12
Not a problem!
Take all the time you need.

---

### Post by lovinglinux on 2010-07-13
OK. Tutorial is up. 

[http://firefox-tutorials.blogspot.com/2010/07/compiling-firefox.html](http://firefox-tutorials.blogspot.com/2010/07/compiling-firefox.html)

I have omitted the PGO part, since it is not working.

I also did some benchmarks and Swiftfox 3.6.3 scored 300 points more than 3.6.6 compiled here on 64bit. Kind of disappointing.

I have completely reinstalled Ubuntu, this time 32bit. Firefox runs better, while Opera and Chrome have a small drop in performance.

I'm currently compiling Firefox 3.6.4 32bit to see if there is any difference. When I had a Pentium 4, the difference was huge. Perhaps I'm not getting the proper optimization or the PGO that makes the difference in Swiftfox.

---

### Post by sandman3838 on 2010-07-13
I'm back!
Sorry for the delay I had some yard work and I went to the gym.

I have a few questions:

1 - Should I go a head and remove Firefox and Swiftfox then install Firefox 3.6.6 now or just wait for PGO part?

2 - You suggested installing Firefox 3.6.6 however the Mozilla site you gave had a 4.0b1 available?  If you do want me to go a head with the install, would you recommend one or the other?

3 - You mention in red:

ac_add_options --enable-official-branding
export CHOST="x86_64-pc-linux-gnu"
export CFLAGS="-march=core2 -O3 -pipe"
export CXXFLAGS="${CFLAGS}"

I have a AMD Chip what should I type in.  See screen shot.

Again thanks for all you help.

---

### Post by lovinglinux on 2010-07-13
> **sandman3838 said:**
> 1 - Should I go a head and remove Firefox and Swiftfox then install Firefox 3.6.6 now or just wait for PGO part?

Firefox is not compiling with PGO here, so I won't publish that part of the tutorial.

> **sandman3838 said:**
> 2 - You suggested installing Firefox 3.6.6 however the Mozilla site you gave had a 4.0b1 available?  If you do want me to go a head with the install, would you recommend one or the other?

If you don't have many extensions and themes, I would recommend going for 4.0b1. It runs faster than Swiftfox or  Firefox 3.6.6 compiled with optimizations and you don't have to compile.

I haven't tested it extensively, but you can install it manually, by simply extracting it to /opt folder or even your home folder. If you don't find any problems, then stick with it. See instructions at [http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html)

You can also find instructions on that tutorial on how to disable extension compatibility check, in case you have extensions that doesn't work.

> **sandman3838 said:**
> 3 - You mention in red:

ac_add_options --enable-official-branding
export CHOST="x86_64-pc-linux-gnu"
export CFLAGS="-march=core2 -O3 -pipe"
export CXXFLAGS="${CFLAGS}"

I have a AMD Chip what should I type in.

I forgot to put the link to AMD flags. Already updated the tutorial. The link is [http://en.gentoo-wiki.com/wiki/Safe_Cflags/AMD](http://en.gentoo-wiki.com/wiki/Safe_Cflags/AMD) 

It would be:

```
export CHOST="x86_64-pc-linux-gnu"
export CFLAGS="-march=k8 -O2 -pipe"
export CXXFLAGS="${CFLAGS}"
```

I must admit that when I wrote that tutorial for the first time Firefox was still version 3, which is a lot slower and I had a Pentium 4 single core, so compiling it made a huge difference. Unfortunately, the same didn't happen now in my 64bit machine.

I tried to compile it for 32bit, now that I reinstalled Ubuntu, but I'm getting Segmentation faults. I'm probably using the wrong flags, since my CPU is 64bit but Ubuntu 32bit.

---

### Post by lovinglinux on 2010-07-14
Just an update about Firefox 4.0. Probably several extensions won't work even with compatibility check disabled, because the extension manager changed a lot. You need to test them on a clean profile, otherwise you might think they are working properly, when in fact they aren't, because some of their properties might not being updated. For example most of my extensions check for version when you install or update, in order to provide the necessary changes according to the extension version. This info is not even created on a new profile and the extension doesn't work, but when you use the same profile on FF 4, the extension works, but the version info is not updated, which might cause problems.

---

### Post by sandman3838 on 2010-07-14
I'm back...

I downloaded firefox-4.0b1.tar.bz2 and I'm tying to install the Firefox 4.0.  After extracting, it I now have a firefox folder in my home directory.

About the compiling page, I made/saved this for the .mozconfig file:

. $topsrcdir/browser/config/mozconfig
export MOZILLA_OFFICIAL=1
export BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
mk_add_options BUILD_OFFICIAL=1
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-@CONFIG_GUESS@
ac_add_options --enable-official-branding
export CHOST="x86_64-pc-linux-gnu"
export CFLAGS="-march=k8 -O2 -pipe"
export CXXFLAGS="${CFLAGS}"
export CPPFLAGS="${CFLAGS}"
ac_add_options --enable-application=browser
mk_add_options MOZ_CO_PROJECT=browser
ac_add_options --enable-optimize 
ac_add_options --enable-default-toolkit=cairo-gtk2
ac_add_options --enable-system-cairo
ac_add_options --enable-xft
ac_add_options --enable-extensions=default
ac_add_options --enable-strip
ac_add_options --enable-install-strip
ac_add_options --enable-pango
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --disable-necko-wifi
ac_add_options --disable-tests
ac_add_options --disable-accessibility
ac_add_options --disable-installer
ac_add_options --disable-crashreporter
ac_add_options --disable-parental-controls
ac_add_options --enable-printing
ac_add_options --with-pthreads

However:

After configuring the .mozconfig for your processor and preferences, save it and run the following commands:
cd ~/mozilla-x.y.z
make -f client.mk build

What I get is this:

keivn@kj-desktop:~$ cd ~/firefox

keivn@kj-desktop:~/firefox$ make -f client.mk build
make: client.mk: No such file or directory
make: *** No rule to make target `client.mk'.  Stop.
keivn@kj-desktop:~/firefox$ 

What am I not understanding?

Now I need to tell you that I did run Firefox 4 from terminal and there were some issues about certain web sites were unavailable like Youtube and all but two of the plugins & Addons were unavailable,  Perhaps if I would have been able to complete the process the results might have been different?

I do have 3.6.6 installed/remaining, I installed it again through Synapic and it running just fine even though its slower that Swiftfox.  Swiftfox not Firefox 3.7 are no longer in the system.  Would applying the .mozconfig alterations to Firefox 3.6.6 help that version?  I mean except for the speed everything is running.  


Just a thought?

---

### Post by Mahngiel on 2010-07-14
> **sandman3838 said:**
> Back again.

Here is an update.

Since my original posting on this I did some reading around and I found that using FLASH AID could correct my issue.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)


Seems you've made progress on your initial issue.  Just wanted to let you know i was having a similar problem with FF and Flash, though slightly different.  I used your link, and after a quick restart, was able to stream flash again.  Thanks.

---

### Post by lovinglinux on 2010-07-14
> **sandman3838 said:**
> What I get is this:

keivn@kj-desktop:~$ cd ~/firefox

keivn@kj-desktop:~/firefox$ make -f client.mk build
make: client.mk: No such file or directory
make: *** No rule to make target `client.mk'.  Stop.
keivn@kj-desktop:~/firefox$ 

What am I not understanding?

Looks like you extracted and are trying to compile a Firefox tar.bz2 file that do do not contain source code. Mozilla distributes Firefox source just like it distributes executable binaries. The source code has "source" in the tar.bz2 fie name. This, when extracted, will create a folder named ~/mozilla-1.9.2 or similar, while the executables will create a folder ~/firefox.

> **sandman3838 said:**
> Now I need to tell you that I did run Firefox 4 from terminal and there were some issues about certain web sites were unavailable like Youtube and all but two of the plugins & Addons were unavailable,  Perhaps if I would have been able to complete the process the results might have been different?

No. It has nothing to do with the compilation. The problem is that Firefox 4 introduces major changes in the extension API, so extensions break even if you are able to disable compatibility check.

> **sandman3838 said:**
> I do have 3.6.6 installed/remaining, I installed it again through Synapic and it running just fine even though its slower that Swiftfox.  Swiftfox not Firefox 3.7 are no longer in the system.  Would applying the .mozconfig alterations to Firefox 3.6.6 help that version?  I mean except for the speed everything is running. 

So you fixed it. That's great news. Compiling Firefox 3.6.6 (mozconfog stuff) could help, but as I said earlier, I didn't see much difference on 64bit system.

I would stick with 3.6.6 from the repositories and wait for the official release of Firefox 4.0, when most active extensions should be updated to work with it. Firefox 4 will also have Tracemonkey enabled on 64bit, so it will be much faster than the current version of Swiftfox.

Sorry, looks like we ended up where we started, but at least 3.6.6 is working now.

---

