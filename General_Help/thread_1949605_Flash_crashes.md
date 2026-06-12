---
title: "Flash crashes"
date: 2012-03-30
forum: General Help
---

### Post by atticadayz on 2012-03-30
I've tried it in all browsers and other sites besides youtube, but it always crashes.
I've look around for a fix but none of them worked. It just began today, out of the blue. I've reinstalled flash as well.

---

### Post by Andrew_P on 2012-03-30
> **atticadayz said:**
> I've tried it in all browsers and other sites besides youtube, but it always crashes.
I've look around for a fix but none of them worked. It just began today, out of the blue. I've reinstalled flash as well.

Adobe [Macromedia] Flash is a piece of junk &#8212; it always has been [since it was created in the mid 1990s]("http://en.wikipedia.org/wiki/Adobe_Flash#History").  This has been a known problem for a long time.  Macromedia fiddled with it for years before Adobe bought the company, and continued to fiddle with it.  Since they haven't been able to make it stable and reliable in 15 years of trying, presumably they never will.

Firefox has attempted to remedy this by segregating external applications in "sandboxes", so that if or when they crash, they don't cause the browser to crash as well.  I don't know how successful this effort has been.  I use Mozilla SeaMonkey, which uses much of the core code from Mozilla Firefox, but Flash frequently crashes the browser with memory leaks so severe that is takes down the operating system as well, requiring a cold restart of the machine.

In the past, when this happened on an old Windows 98SE system that I still own and run, the solution was to find an old Flash installer and perform a manual installation of the last known version that didn't crash as often, then refuse "upgrades" from Adobe for 4-6 months, or until Web sites began to complain that my version of Flash was too old and refuse to serve content.  It seems they push out versions that are buggier than their standard buggy product on a regular basis and it takes them several months to fix them and make Flash usable again.

So many Web sites today use Flash content that it's like playing Russian Roulette with three out of six chambers loaded.  You might consider installing a Flash Blocker plug-in to prevent flash content from loading until you click the icon in the Web page.

Last year the late Steve Jobs said that Flash would never be made available on the iPhone or iPad, because it was a resource hog and shortened battery life.  The instability of Flash may have been another reason he shunned it.

The much-vaunted HTML5 that is supposed to make Flash obsolete isn't a solution, either.  Sites that use it in place of Flash are verrrrry sloooow and bring my computer to its knees.  It's so bad that I've disabled HTML5 support in SeaMonkey.

---

### Post by atticadayz on 2012-03-30
What can I do to keep it from crashing?

---

### Post by idoitprone on 2012-03-30
> **Andrew_P said:**
> Adobe [Macromedia] Flash is a piece of junk — it always has been [since it was created in the mid 1990s]("http://en.wikipedia.org/wiki/Adobe_Flash#History").  This has been a known problem for a long time.  Macromedia fiddled with it for years before Adobe bought the company, and continued to fiddle with it.  Since they haven't been able to make it stable and reliable in 15 years of trying, presumably they never will.

Firefox has attempted to remedy this by segregating external applications in "sandboxes", so that if or when they crash, they don't cause the browser to crash as well.  I don't know how successful this effort has been.  I use Mozilla SeaMonkey, which uses much of the core code from Mozilla Firefox, but Flash frequently crashes the browser with memory leaks so severe that is takes down the operating system as well, requiring a cold restart of the machine.

In the past, when this happened on an old Windows 98SE system that I still own and run, the solution was to find an old Flash installer and perform a manual installation of the last known version that didn't crash as often, then refuse "upgrades" from Adobe for 4-6 months, or until Web sites began to complain that my version of Flash was too old and refuse to serve content.  It seems they push out versions that are buggier than their standard buggy product on a regular basis and it takes them several months to fix them and make Flash usable again.

So many Web sites today use Flash content that it's like playing Russian Roulette with three out of six chambers loaded.  You might consider installing a Flash Blocker plug-in to prevent flash content from loading until you click the icon in the Web page.

Last year the late Steve Jobs said that Flash would never be made available on the iPhone or iPad, because it was a resource hog and shortened battery life.  The instability of Flash may have been another reason he shunned it.

The much-vaunted HTML5 that is supposed to make Flash obsolete isn't a solution, either.  Sites that use it in place of Flash are verrrrry sloooow and bring my computer to its knees.  It's so bad that I've disabled HTML5 support in SeaMonkey.

well, flash is getting better lately. It so much better, that I can say flash is stable. I dont know your problem but flash does not crash as much. The reason why it was a resource hog on a mac was apple's fault. Yes it was apple's fault, since it took them forever to release their hardware acceleration api.
If it was a year ago, flash crashes alot on linux, but lately no.

op you have to update flash

---

### Post by atticadayz on 2012-03-30
I'm running the latest version.

---

### Post by idoitprone on 2012-03-30
> **atticadayz said:**
> I'm running the latest version.

flash version?

---

### Post by atticadayz on 2012-03-30
Adobe flash, 11,2,202,228

---

### Post by idoitprone on 2012-03-30
> **atticadayz said:**
> Adobe flash, 11,2,202,228

yikes, i do not understand what is going on them, because i using that version and it never crashes

---

### Post by atticadayz on 2012-03-30
I've been using it without any problems till now...

---

### Post by pootan on 2012-03-30
There is a known bug with Nvidia cards and hardware acceleration with the latest version of flash. If this is your situation you can try right clicking and disabling it in the flash settings. If that fails then have a look in the Multimedia & Video section of these forums. There are quiet a few threads about it with a few different solutions on the first page.

---

### Post by atticadayz on 2012-03-30
I did come across that solution, I would like to try it but I've never been able to click the settings in flash, it is just unclickable. If there is a way around that I would love to know.

---

### Post by pootan on 2012-03-30
There is a workaround for that. Have a read through this thread and in post 10 you can find a solution that may or may not help. Otherwise you can use one of the other solutions there.

[http://ubuntuforums.org/showthread.php?t=1949137](http://ubuntuforums.org/showthread.php?t=1949137)

---

### Post by Andrew_P on 2012-03-30
> **idoitprone said:**
> well, flash is getting better lately. It so much better, that I can say flash is stable. I dont know your problem but flash does not crash as much. The reason why it was a resource hog on a mac was apple's fault. Yes it was apple's fault, since it took them forever to release their hardware acceleration api.
If it was a year ago, flash crashes alot on linux, but lately no.

op you have to update flash

Flash support for Linux is going away, if it hasn't done so already.  See "[Adobe Tells Linux Users to Switch to Google Chrome for Flash Player Support]("http://www.theinfoboom.com/articles/adobe-tells-linux-users-to-switch-to-google-chrome-for-flash-player-support/")" (March 8, 2012).

What's more, the latest version of the Flash plugin for Firefox/SeaMonkey etc. appears to be broken.  Suddenly, just today, Flash content in Firefox, SeaMonkey and Opera stopped working.  I have Google Chrome installed, but Flash still works in Chrome.  What's up?  I usually accept updates from Adobe and Google without question, but it appears one of them pushed out a new version of libflashplayer.so that no longer works with anything except Google Chrome on Linux.  Fortunately, I have a backup of an earlier installation of Ubuntu and was able to get an early-March 2012 copy of libflashplayer.so to copy into /usr/lib/flashplugin-installer.  (I first renamed "libflashplayer.so" as "libflashplayer.so.latest", then renamed the "libflashplayer.so" old version as "libflashplayer-mozilla-compatible.so".  Finally, I created a symbolic link to libflashplayer-mozilla-compatible.so and renamed it "libflashplayer.so".)  Once I had the older libflashplayer.so in place, Flash content started working again in my other browsers.  The one I'm now using *may be* **11.1.102.62-0lucid1_i386**, dated 15 February 2012, but I'm not sure.  Older plugins for other installations can be found in the Canonical repository at [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/).

As for Flash not crashing as much, I beg to differ.  Adobe pushed out a version about a week ago that was noticeably less stable, causing frequent browser crashes.  Over the years they've produced versions that were so bad that they were simply unusable.  My solution is to install an older version of the Flash Player that still works and keep using it until Web sites start complaining that it's "too old", and refuse to accept updates from Adobe until I know the newer version works again. (You may need a spare system installation to test it before committing to your regular system.)

Now that I got Flash working again, I've disabled the Google Chrome and Adobe repositories in Software Sources to prevent future "updates".  They can do whatever they want, but I'm not buying.

---

### Post by Bromden on 2012-03-30
I've got problems with Flash too. It used to occupy 100% CPU so I had to power off the PC. Actually I'm working on Ubuntu 10.10, and to solve the problem I'm using a Greasemonkey script to watch flash in HTML5 and Gnash. Unfortunately some Flash content and some Vimeo videos can't be loaded...

Good Luck

---

### Post by Andrew_P on 2012-03-30
> **Bromden said:**
> Unfortunately some Flash content and some Vimeo videos can't be loaded...

That's the first inkling I had this morning that something was wrong.  YouTube and other sites with Flash content simply presented a blank panel.  It was working fine yesterday, but suddenly stopped today.  It wasn't crashing, though.  See my solution in my earlier post, immediately above.

---

### Post by idoitprone on 2012-03-30
> **Andrew_P said:**
> Flash support for Linux is going away, if it hasn't done so already.  See "[Adobe Tells Linux Users to Switch to Google Chrome for Flash Player Support]("http://www.theinfoboom.com/articles/adobe-tells-linux-users-to-switch-to-google-chrome-for-flash-player-support/")" (March 8, 2012).

What's more, the latest version of the Flash plugin for Firefox/SeaMonkey etc. appears to be broken.  Suddenly, just today, Flash content in Firefox, SeaMonkey and Opera stopped working.  I have Google Chrome installed, but Flash still works in Chrome.  What's up?  I usually accept updates from Adobe and Google without question, but it appears one of them pushed out a new version of libflashplayer.so that no longer works with anything except Google Chrome on Linux.  Fortunately, I have a backup of an earlier installation of Ubuntu and was able to get an early-March 2012 copy of libflashplayer.so to copy into /usr/lib/flashplugin-installer.  (I first renamed "libflashplayer.so" as "libflashplayer.so.latest", then renamed the "libflashplayer.so" old version as "libflashplayer-mozilla-compatible.so".  Finally, I created a symbolic link to libflashplayer-mozilla-compatible.so and renamed it "libflashplayer.so".)  Once I had the older libflashplayer.so in place, Flash content started working again in my other browsers.  The one I'm now using *may be* **11.1.102.62-0lucid1_i386**, dated 15 February 2012, but I'm not sure.  Older plugins for other installations can be found in the Canonical repository at [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/).

As for Flash not crashing as much, I beg to differ.  Adobe pushed out a version about a week ago that was noticeably less stable, causing frequent browser crashes.  Over the years they've produced versions that were so bad that they were simply unusable.  My solution is to install an older version of the Flash Player that still works and keep using it until Web sites start complaining that it's "too old", and refuse to accept updates from Adobe until I know the newer version works again. (You may need a spare system installation to test it before committing to your regular system.)

Now that I got Flash working again, I've disabled the Google Chrome and Adobe repositories in Software Sources to prevent future "updates".  They can do whatever they want, but I'm not buying.

oh, i guess Adobe really are pulling away their resources. Oh well, it was the only product that I actually stop hating. Now I have to wait until some fix the resource hogs of pdf files

---

### Post by atticadayz on 2012-03-31
I did the round about way of disabling the hardware accelerator, but it didn't do any good. So I downloaded version 11.1.102.63. But, I need a walkthrough on how to install it.

---

### Post by Bromden on 2012-04-01
I'm not sure but follow this instructions:
1) Download the tar.gz
2) Uncompress the tar.gz
3) Take the "libflashplayer.so" file and put it in usr/lib64//mozilla/plugins
(if you have an i386 architecture put it in usr/lib32/mozilla/plugins

It seems to work...

Thank you Andrew_P! ;)

---

### Post by tealex on 2012-04-14
sudo rm /etc/adobe/mms.cfg

---

