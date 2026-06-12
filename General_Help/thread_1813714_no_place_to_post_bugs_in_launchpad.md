---
title: "no place to post bugs in launchpad"
date: 2011-07-28
forum: General Help
---

### Post by AgentZ86 on 2011-07-28
I cannot find where to post bugs in the launchpad anymore ?
What happened to the launchpad ?

It's sort of goofy that there is no (report a bug) link anywhere.

But if you search bugs then you can see a link to the right, but nothing anywhere else
And even then you can only post a bug regarding that same category and subject.

So it would appear the launchpad has a bug, or I just can't figure out how to navigate to report a bug

Please advise

---

### Post by plucky on 2011-07-28
> **AgentZ86 said:**
> I cannot find where to post bugs in the launchpad anymore ?
What happened to the launchpad ?

It's sort of goofy that there is no (report a bug) link anywhere.

But if you search bugs then you can see a link to the right, but nothing anywhere else
And even then you can only post a bug regarding that same category and subject.

So it would appear the launchpad has a bug, or I just can't figure out how to navigate to report a bug

Please advise


Try Alt+F2 and in the window that opens **ubuntu-bug <name of Package>** and see what happens.

Or do the same from a terminal window.

Good Luck

---

### Post by AgentZ86 on 2011-07-28
> **plucky said:**
> Try Alt+F2 and in the window that opens **ubuntu-bug <name of Package>** and see what happens.

Or do the same from a terminal window.

Good Luck

ahh thanks,

but I don't know the name of the package , I can only describe the symptom ?

---

### Post by plucky on 2011-07-28
> **AgentZ86 said:**
> ahh thanks,

but I don't know the name of the package , I can only describe the symptom ?

See  Link

[https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage)

Good Luck

---

### Post by AgentZ86 on 2011-07-28
> **plucky said:**
> See  Link

[https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage)

Good Luck

Well, I do understand what your link is asking me to do to find the package, but the problem is I don't know what package is being executed Because I'm not really the one executing the package by name.

Firefox is executing it and I don't know what firefox is launching ?
I think it's nautilus but not really sure.

For example: 
The web features that ask to attach files on the ubuntu forums,
Or webmail to attach files aka yahoo, 
or images in facebook etc.
You know ? when you want to upload on ebay or something and there is always this field that asks you to browse and you can click browse to that location and a screen comes up for you to select a file.

> When the screen comes up to browse ?  
Which package is being launched here ? 
Is it nautilus ? or something else ?  

If I knew this I could put <nautilus> but I don't know what the web browser is doing or what is being launched

The file browser works perfect when not being launched from the web browser if this is really what the web browser is doing ?

Thanks

---

### Post by mikewhatever on 2011-07-28
If you could just tell what's the problem you experience with Ubuntu without writing dissertations, we could help you figure out the package in question. Seriously, filing a bug report that looks like the post above would be a waist of time.

---

### Post by AgentZ86 on 2011-07-28
Yep, it's true

I did do that but no response and I was once told to file bug report, so I'm sort of in between both topics now

See my post describing the problem:

[http://ubuntuforums.org/showthread.php?t=1813449](http://ubuntuforums.org/showthread.php?t=1813449)

Thanks

---

### Post by mikewhatever on 2011-07-28
Interesting problem, but is it really that urgent that you had to reinstall and open several threads on the subject within 24 hours? I can clearly see window borders and buttons in both screenshots, but regardless, why do you need them, as well as images and colors to attach a file? Just select the file you want attached and be done.

---

### Post by AgentZ86 on 2011-07-30
> **mikewhatever said:**
> Interesting problem, but is it really that urgent that you had to reinstall and open several threads on the subject within 24 hours? I can clearly see window borders and buttons in both screenshots, but regardless, why do you need them, as well as images and colors to attach a file? Just select the file you want attached and be done.

I'm not sure what the heck your looking at but in the images that I posted you can clearly see that on 11.04 there is no borders or buttons just white backround with black text.

I mean don't get me wrong the window itself has a border, but look at the 2 images pretty much everything is missing (upper left top file buttons and navigation for foward and back, no buttons, no button borders, no colors, and non-functional navigation or intermittent navigation.) just look at them again, white with black text only and cannot select or highlight files to upload.

Additionally the navigation is not working when you navigate into the folder tree a bit further it crashes.
At the top where you normally see the folder buttons which show the folder hierarchy you can clearly see buttons and borders in version 10.10 in the images that I have posted. The second images shows the 11.04 and I posted these for comparison. The white backround with black text is not default and there is something obviously wrong with this.

Also there is no ability to select individual files since the highlighting of those selected files are also non-functional. Typically you can use the ctrl+arrow keys or ctrl+mouse or sometimes shft+mouse depending on the application and the file will be highlighted and you can click the OK button. But in this case no highlighting and no real indication that you have selected a file at all. But either way when you click the OK text below where there should be a button, it just crashes to the desktop.

Now having said all that, the system works perfectly otherwise, and it's only this web based call to navigate to browse files that this occurs. Otherwise the file browsing works normally and perfectly as it should. Very strange that only the web based applications is doing this and I have no idea what application is being launched as I mentioned. 

Additionally I did not post these within 24 hours of each other I actually re-worded and edited the original and added images, but the original title did not change in a previous post that was ongoing under the advanced edits, so I posted a new duplicate topic with a new title that was better related to the actual subject since the subject evolved into more of a package or software related to 11.04 and not so much driver related. The actual post started in nvidia drivers for 11.04 earlier then this and evolved to this point.

Since this was originally thought to be something to do with the nvidia cards with no driver support in the new 11.04 do to the newer x.org driver support which is a known issue I was in another chat posting this but after the driver issue became mute, and appeared to be non-related to this subject anymore I posted the new post.
Although the new post appears to be within 24hours of each other they were not because the other post subjects were not the same.

So the subject has now evolved to the point where possibly a bug report should be issued since this is a fresh install with full driver support and does not appear to occur when booting to the flash drive.

I am led to consider that it could be a plugin bug related topic.

Since I cannot seem to get any help determining which application is being launched when the browser launches this file browser, I will likely try to turn off all plugins and work from there and see if I can determine anything else.

There was no urgency I guess, but it is a workstation we use to run parts of our business , however we have other desktops so we are using them until I get this sorted out. I was sort of hoping to solve this prior to purchasing another video card but initially thought that it must be driver support related. Now that the new video card is installed and the problem persists I had thought that perhaps I messed something up while playing with previous drivers and plugins to get the old card working. So I simply did a fresh install and driver support is now confirmed not to be an issue. So it may not have been necessary to re-install but I wanted to be sure that everything was installed that should be installed after messing with other non supported drivers.

So it's back to the original question which is what application is this and where do you file the bug, and how to determine what application is being launched and causing this problem ?

Please advise thanks for the replies.

---

### Post by AgentZ86 on 2011-07-30
The problem is Shockwave 10.3 r181 which is stock with Ubuntu 11.04 64bit version

I have it figured out with the clickety method.
Well it's not fixed but at least I figured out what application or what is the causing this.

Anyhow It's the Shockwave Flash plugin for the browser that is causing this.

Shockwave 10.3 r181

After disabling each plugin in the browser one at a time, then restarting firefox to make the changes, and doing this for each plugin I found that disabling the shockwave flash allows the file navigation to work properly.

So now I guess I can report this bug, and try to apply a fix up.

I have no idea how or why shockwave would cause this or how it relates to launching the file navigation but at least I'm closer now to figuring this out.

Thanks for the help

---

### Post by AgentZ86 on 2011-07-30
However, there is still no place to post bugs in launchpad and track these bugs as before. Is there some place you can post the bugs directly in launchpad pages ? Or is that gone now ? 

Please advise

---

### Post by AgentZ86 on 2011-07-30
Bug posted:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/818595](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/818595)

---

