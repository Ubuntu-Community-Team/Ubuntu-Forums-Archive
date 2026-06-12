---
title: "Are these just typical &quot;new release&quot; bugs?"
date: 2009-10-31
forum: General Help
---

### Post by solwic on 2009-10-31
Did a clean install of Karmic yesterday, and when I first booted up, everything was awesome.  It was fast, and clean, and sleek.  Very cool.

Then I settled in and started "using" Karmic instead of "checking it out".  That's when all the problems started.

Now, don't get me wrong.  I'm not bashing Karmic/Ubuntu/Linux. I'm just wondering if the issues I ran into are the run-of-the-mill new release glitches, or if these are problems that will be, by and large, ignored (like the hibernate feature pre-9.10).  

1.  Saving settings.  I would change the volume in the volume preferences, turn off animations in compiz, and when I rebooted, they were all back to the default. 

2.  Rhythmbox.  This could be an extension of 1, but normally when I added my library to Rhythmbox, it would ask me to search for a codec every time it hit a .wma file.  I'd have to click cancel each time it asked, so usually I click cancel 30 or 40 times when I first load my library.  But after that, it didn't bug me anymore. In Karmic, I had to do it every time I closed/opened Rhythmbox....

3.  Hotkeys.  In Jaunty, my media hotkeys worked great with Rhythmbox and Exaile.  In Karmic, they quit working in Exaile, which forced me to use Rhythmbox, which led me to the codec issue....

4.  Sluggish.  At first it was super quick, and then it started to slow down. Jaunty actually boots faster than Karmic for me, and the only significant decrease in speed with Jaunty is not having Firefox 3.5 (which was uber fast), though I'm sure there's a way I can get 3.5 in Jaunty....

5.  Empathy.  Not only is Empathy no match for Pidgin, but I couldn't find any way to turn it off.  I added Pidgin to the bootup menu, but it still loaded with Empathy, which was annoying.  This is the first time Ubuntu has crammed a program down my throat, and it leaves the same bitter taste I had when Windows did it....

6.  Normally, my wireless connection gets dropped once in Jaunty.  I'll boot up, connect, then it'll disconnect and reconnect, and then I'm good until I boot up again.  With Karmic, I was constantly being dropped, about once an hour. 

I'm back with Jaunty for now.  Maybe I'll give Karmic another shot in a couple of months.  Anybody else having these, or similar, issues?  Is this just typical bug stuff?

---

### Post by scouser73 on 2009-10-31
The boot time in Karmic has increased (for me anyhow), Jaunty gave me 21 seconds from boot to desktop, with Karmic it's 1.05 minutes from boot to desktop.  Apart from that everything works fine.

---

### Post by misfitpierce on 2009-10-31
A lot are minor bugs messing with other things... You shouldn't have to wait more than a month most likely... I say about a month or so most of the big bugs will be terminated in 9.10. Got people reporting bugs and trying to help with them so fixes will be shooting out asap.

---

### Post by Leed on 2009-11-01
I have some of those problems too

-Boot time has extremely increased, I also get an error message saying something about fstab waiting for all my partitions, the message comes several time and seems to be the cause for delay

-The new volume control has as good as no options

-The very much desired feature in the shutdown menu, that lets me switch off the annoying shutdown delay is gone... I had to manually edit gconf

-I can't install dontzap, I want my ctrl+alt+backspace back... why do the devs have to take these good things away?

-Empathy is absolutely no benefit towards pidgin (and yes, I can't switch it off either). The smiley menu is totally hidden, the layout is worse, I find nothing better in it.


I was really looking forward to Karmic, but now I'm going to keep my other PCs running Jaunty until Karmic shows some big improvements

---

### Post by kircher on 2009-11-01
At first I really liked Karmic. It seems faster and smoother on this computer than any other version I've used. And for the first time ever, everything worked out-of-the-box. No screwing around at all. But I have encountered a major bug, resulting in my system completely freezing/crashing and I have to restart manually to get it to work again. I use wireless 802.11 for internet access and believe it's the wpa_supplicant causing my problems. Here is my thread [http://ubuntuforums.org/showthread.php?t=1308826](http://ubuntuforums.org/showthread.php?t=1308826)

and another similar thread [http://ubuntuforums.org/showthread.php?t=1306535&page=2](http://ubuntuforums.org/showthread.php?t=1306535&page=2)

This distro seems to be very buggy.

---

### Post by miklcct on 2009-11-01
I consider Karmic a very stable release. It no longer has random freezes, Plasma no longer crashes, Konqueror has improved a lot, etc.

---

### Post by kircher on 2009-11-01
> **miklcct said:**
> I consider Karmic a very stable release. It no longer has random freezes, Plasma no longer crashes, Konqueror has improved a lot, etc.

I believe it will be a good release. Everything else is good. But I get freezes often.

---

### Post by mozillalives on 2009-11-04
What do you mean "can't turn empathy off"? I had pidgin set to start automatically before I upgraded and it still was my default. I turned it off though because I like empathy and it's support of themes. (Seriously pidgin this is basic stuff.)

---

### Post by Leed on 2009-11-05
> **mozillalives said:**
> What do you mean "can't turn empathy off"? I had pidgin set to start automatically before I upgraded and it still was my default. I turned it off though because I like empathy and it's support of themes. (Seriously pidgin this is basic stuff.)

Very simple, when you close the window empathy is just gone, there's no icon there telling you, that you are still online, no option to close the program down properly. Only if you click on the Mail icon you'll notice it's still on because the menu entry looks a little differen... but still no options to switch it off. As PC user I want to know if a program is still on or not, I don't want it hiding in the background somewhere. 

Also the icon from Pidgin shows you if someone has dropped you a message or not. When working on several desktops this comes very handy. Especially if a Pidgin window is already open on one of the desktops (meaning it won't appear and focus on the desktop you're working on).

I don't get it why Empathy should be better, smiley icons are hidden in some menu, pictures of contacts are shown smaller and take longer to load. Appart from that it looks nearly identical to pidgin.

---

### Post by Mark Phelps on 2009-11-05
> **solwic said:**
>  ... I'm back with Jaunty for now.  Maybe I'll give Karmic another shot in a couple of months.  Anybody else having these, or similar, issues?  Is this just typical bug stuff?

I've been "upgrading" since 7.04 and, after 8.04, my own experience was that each upgrade was increasingly worse (in terms of stuff that no longer worked) than the previous.

The 9.04 version has become infamous for ATI and Intel video driver related problems that left lots of people with a flashing cursor instead of a desktop, or tool away their special effects.

The 9.10 version, especially with the introduction of GRUB2, and apparently some NEW video driver problems, seems to be doing even worse!

So, in answer to your original question, yes, these are typical of bugs seen just after the rollout of a new Ubuntu version.

In all fairness to Canonical, they can only test so much before deploying a new release.  We're not hearing from the folks whose upgrade/install went well; we're only hearing from those with problems.  And, in all too many cases, those people have some combination of the following (1) dual-boot, (2) Wubi, (3) Windows 7.

But these kinds of problems are why I generally advise folks to wait a month or so before upgrading just to watch the forums for problems before doing so.

---

### Post by zuerston on 2009-11-05
There certainly are bugs galore! I outlined some in another post.
[http://ubuntuforums.org/showthread.php?p=8248707#post8248707](http://ubuntuforums.org/showthread.php?p=8248707#post8248707)

---

### Post by Wandel on 2009-11-05
> **Leed said:**
> Very simple, when you close the window empathy is just gone, there's no icon there telling you, that you are still online, no option to close the program down properly. Only if you click on the Mail icon you'll notice it's still on because the menu entry looks a little differen... but still no options to switch it off. As PC user I want to know if a program is still on or not, I don't want it hiding in the background somewhere. 

Also the icon from Pidgin shows you if someone has dropped you a message or not. When working on several desktops this comes very handy. Especially if a Pidgin window is already open on one of the desktops (meaning it won't appear and focus on the desktop you're working on).This annoys me to no end. I could probably live with Empathy, if I only could get it to not hide behind the mail icon.

---

### Post by ManiacDan on 2009-11-05
In my experience, the install seems to get worse before it gets better.  I had some initial upgrade problems related to GRUB not seeing 9.10, I had to manually install grub2 using a liveCD, then everything was great.  I was really happy with 9.10.

Then Flash started taking 100% CPU whenever it ran, so I re-installed flash.

Then Pidgin started taking 150% CPU whenever a new message window opened, so I had to re-install pidgin.

Then my network drives started randomly disconnecting.

Then my Java applications couldn't write to the filesystem.

It's like Canonical tests the new version for 11 minutes before releasing.  

I'm also having random sound issues (works for a few minutes then dies) and the "saving settings" bug plagues me as well, my dual-monitor setup reverts back to cloned displays every time I boot.  I'll have to remember to wait a month before upgrading to L{adjective} L{animal}

-Dan

---

### Post by seenthelite on 2009-11-06
> **Mark Phelps said:**
> I've been "upgrading" since 7.04 and, after 8.04, my own experience was that each upgrade was increasingly worse (in terms of stuff that no longer worked) than the previous.

The 9.04 version has become infamous for ATI and Intel video driver related problems that left lots of people with a flashing cursor instead of a desktop, or tool away their special effects.

The 9.10 version, especially with the introduction of GRUB2, and apparently some NEW video driver problems, seems to be doing even worse!

So, in answer to your original question, yes, these are typical of bugs seen just after the rollout of a new Ubuntu version.

In all fairness to Canonical, they can only test so much before deploying a new release.  We're not hearing from the folks whose upgrade/install went well; we're only hearing from those with problems.  And, in all too many cases, those people have some combination of the following (1) dual-boot, (2) Wubi, (3) Windows 7.

But these kinds of problems are why I generally advise folks to wait a month or so before upgrading just to watch the forums for problems before doing so.
  
I am curious about the comments regarding dual-boot etc etc potentially causing bugs or problems with peoples installations of 9.10. Is there a more technical explanation of why this is the case. I am dual booting and have been considering doing a full installation of Ubuntu and removing Vista.

---

### Post by Kaneda187 on 2009-11-06
> **seenthelite said:**
> I am curious about the comments regarding dual-boot etc etc potentially causing bugs or problems with peoples installations of 9.10. Is there a more technical explanation of why this is the case. I am dual booting and have been considering doing a full installation of Ubuntu and removing Vista.

dont do it.

---

### Post by QLee on 2009-11-06
> **seenthelite said:**
> I am curious about the comments regarding dual-boot etc etc potentially causing bugs or problems with peoples installations of 9.10. Is there a more technical explanation of why this is the case. I am dual booting and have been considering doing a full installation of Ubuntu and removing Vista.

You might want to reread what Mark Phelps wrote.

Nothing is said about those *causing* problems. The thing is that those configurations are more complex than a single boot system and people who don't yet have sufficient knowledge make mistakes, that's the "technical" you were asking about. People who do know enough, usually can easily trace and correct the problems they encounter. The Ubuntu Installer will usually install everything correctly on a single OS computer if it doesn't have hardware too new for the kernel version. But, of course, on a help forum, you are very likely to see failures rather than successes and many of them relate to skill level.

---

### Post by fluffman86 on 2009-11-06
Karmic is awesome for me.  Why?  Because I've been testing it since Alpha 3 when things WERE broken.  Then I filed bug reports against problems with my hardware, and things got better.  

So really, don't expect a lot of bug fixes now that testing is over.  If your computer didn't work with Karmic during the Beta or the RC, then it's probably not going to work.

But don't lose hope though! Keep an install of it lying around, and keep filing bugs.  That way, Ubuntu will have a whole 6 months of testing by the time they are ready to roll out Lucid Lynx 10.4. :D  And when you're able, start testing that as well, maybe using virtualbox to start with.

As for long boot times/grub problems.  I had much longer boot times on my desktop than on my laptop to begin with.  Then I noticed that Ubuntu booted quickly, but grub was taking a long time to load.  If you have more than 1 hard drive, try booting into your BIOS and changing the boot order of your hard drives.  Turns out, grub was having trouble finding itself because it looked on my primary hard drive first, then looked on my secondary drive where ubuntu and /boot were.  Switched it and now I have a 30 second boot.

For empathy: yeah, it sucks.  We had a huge discussion about this, but canonical and the ubuntu developers at the Ubuntu Developer Summit had already made their decision.  Personally, I think it was the wrong one, and they should have kept pidgin over empathy (and should go with banshee over rhythmbox :P while they're at it!).  But not to fret, just run:
```
sude apt-get remove empathy
```
and it's gone.  You can keep using pidgin no problem.

---

