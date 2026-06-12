---
title: "Can't get Dell 5650 Speakers to Work"
date: 2006-04-13
forum: General Help
---

### Post by DE Retiree on 2006-04-13
Hi, I'm pretty new to linux and ubuntu.  Installed Breezy on my Dell 8400 with Dell 5650 5.1 surround speakers.  Can't get speakers to work?  I searched forum but could not find any help.  Also have read "Beginning Ubuntu Linux" by Keir Thomas but did not get any ideas there.  Maybe speakers are not compatible??

Thanks,   DE Retiree

---

### Post by DE Retiree on 2006-04-13
Hey folks,

Any ideas on  my problem?

Thanks.

DE Retiree

---

### Post by rabidphage on 2006-04-13
please be more specific if you want help
like what kind of hardware you are running??
whats the soundcard
and stuff like that.......

u could confuse people you see
i was tempted to answer you like this
"why take the trouble??? leave your stubborn speakers at home"

no offence mate just a bad joke:mrgreen:

---

### Post by DE Retiree on 2006-04-14
Sorry for lack of information in original post.  Here are some hardware specs:

Dell Dimension 8400 Series that is about one year old

Intel Pentium 4 Processor 550, 3400 MHz, 1MB Cache

2048 MB System DDR2 RAM at 400 MHz

128 MB PCI Express x16 ATI Radeon X300 SE video

Dell 1905 Flat Panel Monitor, 1280x1024 Resolution, 32 bit color

Creative Labs Sound Blaster Live Audigy LS Series 24bit on PCI bus 4 - also has factory installed audio on motherboard that is currently disabled (I use the Sound Blaster card)

Dell 5650 5.1 Surround Sound Speakers with Subwoofer

My problem is that I get no sound when running Ubuntu on a dual boot system with Windows XP Home edition.  I have Ubuntu on a separate hard drive with no other operating systems on that drive and use the GRUB boot loader to select which system to use.

Please let me know if I can provide additional info.  Thanks again for any suggestions that will help me figure out how to enable sound with Ubuntu.  Please excuse me as I'm a really new linux/ubuntu noobie!

DE Retiree

---

### Post by krismatth3 on 2006-04-14
Check _all_ the mixer settings. (Right click the little speaker icon in the upper right hand corner of the screen in gnome and choose the 'open controls' or similar to open the full mixer.) (Or press Alt+F2 and type "gmixer" then hit enter.)

Once in the mixer, go to Edit->Preferences and check all the items. Then click OK and look at them all. Are there any called "External Amp"? If so, you may need to uncheck that. (That's what works for my Gateway 3520gz laptop.) All in all, play around in there - make sure audio isn't accidentally muted, etctera.

---

### Post by rabidphage on 2006-04-14
Read this might help
[http://ubuntuforums.org/showthread.php?t=75955](http://ubuntuforums.org/showthread.php?t=75955)

I'm a noob as well. just being a search engine for the time being... ;)

---

### Post by DE Retiree on 2006-04-15
Thanks a million folks.  I followed the instructions by teshue in the previous link and it worked.  I never would have figured that out on my own.  Thanks again for the help.

DE Retiree

---

### Post by DE Retiree on 2006-04-15
And, thanks to rabidphage for the link.  Really good help.

DE Retiree:)

---

