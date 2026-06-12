---
title: "Ubuntu Live 8.04"
date: 2011-06-28
forum: General Help
---

### Post by flash_light on 2011-06-28
I got a Intel d915gux motherboard PC. It uses PATA for the HDD and optical drive. I have 2 Gb of memory. 
 
I click on Install Live Without Any Changes To The Computer.
 
I opened the Command Prompt. I typed mkdir scrds_l. I typed cd scrds_l. 
 
I opened Computer to see if it created a directory. It did.
 
I minimized the windows. I then click on Firefox. The optical drive light is flashing and the mouse icon is looping. I wait and wait and wait...too much time goes by and I try to exit and Ubuntu won't let me.
 
My only option is to turn the power off to the PC. I do and restart the PC.
 
Here's the problem: Installing Ubuntu Live has made a change to my PC. The change is with the systems bios. The optical drive no longer is recognized as a boot priority.
 
Being that the optical is no longer recognized I cannot live install again.
 
I am now going to have to restore the bios in order to fix the problem. 
 
Installing Ubuntu Live says it won't make any changes to the PC; so, why did it lie and make changes to the PC?

---

### Post by psusi on 2011-06-28
A few things:

1)  You *try* the live system; you do not install it.

2)  8.04 is over 3 years and 6 releases old.  It is quite depreciated.

3)  It can't change your bios settings.  If your boot priority changed, then either you changed it, or you have a hardware failure.

---

### Post by flash_light on 2011-06-29
> **psusi said:**
> A few things:
 
1) You *try* the live system; you do not install it.
 
2) 8.04 is over 3 years and 6 releases old. It is quite depreciated.
 
3) It can't change your bios settings. If your boot priority changed, then either you changed it, or you have a hardware failure.
 
1) Anyone can try the live system and if happy with it then install from the desk icon.
 
2) D915GUX is an old motherboard and 8.04 is a newer release than this old MB. 
 
3) Ubuntu did alter the bios. As for the bios settings everything else looks good. The bios still recognizes the optical. It's just that the optical is no longer noticed as a boot priority.
 
I did not make any changes to the system bios.
 
I cannot remove the optical as a boot priority unless I unplug the optical drive; therefore, rendering no drive. Having no drive means I would be unable to read from the DVD; therefore, I would not be able to load the Live Ubuntu Install. 
 
As for hardware failure, I would think if the hardware has failed it would never work again. Upon restoration of the bios the optical is now recognized again as a boot priority; therefore, I can try again.
 
I decided to try the Live installation because I didn't want any changes to occur. I tried an installation from the desktop icon and the DVD menu and both times Ubuntu has altered the bios and was unable to fully install. Installation just chokes with no explanations. 
 
I think I have tried Ubuntu Live Install before on this PC. I would go online with Firefox. It's just this time I wanted to see if the command window would work as I am attempting to put together a dedicated game server. I cannot until I install Linux. I was testing first. I needed to find a link to write it down for later. Firefox choked for some reason and Ubuntu would not shutdown and I had to reset the PC. Perhaps I should have closed the other windows instead of minimized.
 
Still my question remains unanswered, Why did Ubuntu Live Install alter my bios when it says, Install Live Without Any Changes To Your Computer?
 
Just thinking outloud, perhaps if the crash did not occur it would have restored the change it made upon shutdown and we would be none the wiser.

---

### Post by psusi on 2011-06-29
> **flash_light said:**
> 1) Anyone can try the live system and if happy with it then install from the desk icon.

By definition, a live system is running from the cd.  Once you install to your disk, you no longer have a live system, so the term "installed live system" is an oxymoron.  You either run the system live, or you install it to the hard disk; the two are mutually exclusive.

> **flash_light said:**
> 2) D915GUX is an old motherboard and 8.04 is a newer release than this old MB. 

So?  That doesn't change the fact that 8.04 is depreciated and only partially supported on servers.  The desktop packages are no longer supported.

> **flash_light said:**
> 3) Ubuntu did alter the bios. As for the bios settings everything else looks good. The bios still recognizes the optical. It's just that the optical is no longer noticed as a boot priority.

No it did not because that is not even possible.
 
> **flash_light said:**
> I did not make any changes to the system bios.
 
I cannot remove the optical as a boot priority unless I unplug the optical drive; therefore, rendering no drive. Having no drive means I would be unable to read from the DVD; therefore, I would not be able to load the Live Ubuntu Install. 

What?  that doesn't make sense.  You said the problem is that the drive already is not a boot priority, so why would you remove it?

> **flash_light said:**
> I decided to try the Live installation because I didn't want any changes to occur. I tried an installation from the desktop icon and the DVD menu and both times Ubuntu has altered the bios and was unable to fully install. Installation just chokes with no explanations. 

If you don't want any changes made, then you don't want to install, which by definition, changes your system.

> **flash_light said:**
> Still my question remains unanswered, Why did Ubuntu Live Install alter my bios when it says, Install Live Without Any Changes To Your Computer?

Once again, this phrase is nonsense.  The definition of installing Ubuntu is changing your computer.  The choices when you boot the livecd are to TRY it without making changes, or to INSTALL it.  The two choices are mutually exclusive.

---

### Post by psusi on 2011-06-29
Because your question is argumentative nonsense.  It is like complaining that a car broke down while you were flying under water.  And now that someone has pointed out that not only do cars not fly, but by definition, if you were under water at the time, you were not flying, and you go all offensive.

For anyone to give you an answer they have to understand what happened, which they can't as long as you keep claiming things that are contradictory or impossible with very little detail.

---

### Post by mörgæs on 2011-06-29
How does it work in a live boot of 10.10 or 11.04?

---

### Post by dFlyer on 2011-06-29
> **flash_light said:**
> 1) Anyone can try the live system and if happy with it then install from the desk icon.
 
2) D915GUX is an old motherboard and 8.04 is a newer release than this old MB. 
 
3) Ubuntu did alter the bios. As for the bios settings everything else looks good. The bios still recognizes the optical. It's just that the optical is no longer noticed as a boot priority.
 
I did not make any changes to the system bios.
 
I cannot remove the optical as a boot priority unless I unplug the optical drive; therefore, rendering no drive. Having no drive means I would be unable to read from the DVD; therefore, I would not be able to load the Live Ubuntu Install. 
 
As for hardware failure, I would think if the hardware has failed it would never work again. Upon restoration of the bios the optical is now recognized again as a boot priority; therefore, I can try again.
 
I decided to try the Live installation because I didn't want any changes to occur. I tried an installation from the desktop icon and the DVD menu and both times Ubuntu has altered the bios and was unable to fully install. Installation just chokes with no explanations. 
 
I think I have tried Ubuntu Live Install before on this PC. I would go online with Firefox. It's just this time I wanted to see if the command window would work as I am attempting to put together a dedicated game server. I cannot until I install Linux. I was testing first. I needed to find a link to write it down for later. Firefox choked for some reason and Ubuntu would not shutdown and I had to reset the PC. Perhaps I should have closed the other windows instead of minimized.
 
Still my question remains unanswered, Why did Ubuntu Live Install alter my bios when it says, Install Live Without Any Changes To Your Computer?
 
Just thinking outloud, perhaps if the crash did not occur it would have restored the change it made upon shutdown and we would be none the wiser.

It makes no changes to your bios. If your battery is dead that will alter your bios.

---

### Post by dmizer on 2011-06-30
While it may seem nitpicky, it's important to get terms correct.

Live session = running only from the CD or DVD.
Install = install to hard disk.

If you did an "install" then Ubuntu can make changes to your system. If you only ran the Live session, then Ubuntu can't (and didn't) make changes to your system. I am assuming by your description that you did not perform an "install" despite the fact that you placed this thread in the "install" section of the forums and also despite the fact that you use the term "install". Since you indicate that, after running a live session of Ubuntu, your boot order appears to have changed there must be some other cause because as others are saying here, it is not possible for an Ubuntu live session to make changes to the BIOS.

Something else caused your BIOS boot order to function differently after having run a live session of Ubuntu.

I'm moving this thread to the "General" section of the forums in an effort to clear up some of the confusion here.

---

### Post by mastablasta on 2011-06-30
I don't know the specs, but i would suggest using 10.04 version. Unless you are using some 486 processor in which case i suggest you try Debian Stable or Crunchbang.
 
They wrote a nice manual with lots of pictures for it (see my signature) and should help you to get started with the basics and help you in instalation.

---

