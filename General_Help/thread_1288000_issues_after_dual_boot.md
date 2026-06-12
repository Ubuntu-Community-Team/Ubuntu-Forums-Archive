---
title: "issues after dual boot"
date: 2009-10-10
forum: General Help
---

### Post by babygenius55 on 2009-10-10
Ubuntu was working like a charm up until I decided to install windows along side and dual-boot. Now after everytime I go into windows, and sometimes even when I just reset the PC When I get to the gui(Desktop) all of my files are locked and many services don't start, the pop-up windows ask me if I want to delete the thing that messing up. I never do. Also I have to use a dock program, or press the power button to get the restart/shutdown etc menu to pop up. Upon rebooting from that state the pc has to go through an 'fsck', and it doesn't work all of the time. Most recently I had to reboot 3 times in a row so the system would start normally.
 
Things I've done that could have caused this-edited the grub file to uncomment the chainloader section and made it +5 as opposed to the +1 that's usually there, that made no difference that i could see. I didn't reactivate the Main Ubuntu partition, which I think may be my problem, but I'm not sure. If you need any more info please let me know.
 
I didn't see anywhere that I am supposed to reactivate the ubuntu partition, but the more I think about it the more I think I should just check the partitions.
 
also, how do you change the position of OS/kernel choice in the grub menu

---

### Post by quixote on 2009-10-11
Windows wants to be the first OS in an installation.  If you install it second, there's always a bunch of grief.  (Happens because it was originally for single computers (DOS), not networked computers like linux / unix.)  There's a lot of information here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) .  Check out especially the section under "Restoring Grub" about 1/4 of the way down.

Can you boot into Windows via grub?  If not, how are you getting into Windows?  Or aren't you?  I would revert chainloader to +1.  Why did you put it to +5?

Not sure what you mean by "reactivate ubuntu".  No, you shouldn't need to do that.  

Grub decides which will be the default boot choice by a line "default=0" up near the beginning of /boot/grub/menu.lst.  It counts from "0", so that would mean the first choice in the list of possible boot choices, usually toward the end of the menu.lst file.

---

### Post by babygenius55 on 2009-10-12
> **quixote said:**
> Windows wants to be the first OS in an installation.  If you install it second, there's always a bunch of grief.  (Happens because it was originally for single computers (DOS), not networked computers like linux / unix.)  There's a lot of information here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) .  Check out especially the section under "Restoring Grub" about 1/4 of the way down.

Can you boot into Windows via grub?  If not, how are you getting into Windows?  Or aren't you?  I would revert chainloader to +1.  Why did you put it to +5?

Not sure what you mean by "reactivate ubuntu".  No, you shouldn't need to do that.  

Grub decides which will be the default boot choice by a line "default=0" up near the beginning of /boot/grub/menu.lst.  It counts from "0", so that would mean the first choice in the list of possible boot choices, usually toward the end of the menu.lst file.


Ok, I can boot into windows VIA grub just fine. The problem comes after I do that.

By reactivate I meant make the Linux partition the actual boot partition, I've since seen that the Windows partition is flagged as the boot partition. I'm going to try changing that first. It should have occured to me since I changed it manually, I would have to put it back.

I put it at +5 because the tutorial I followed informed me that I could put the new windows install in any position on the grub list, but didn't note how. I just assumed (:( I know) That since +1 was the only actual number there, that  that was what it was for. 

Going to check out your link before I make any changes, thank you for the response.

---

### Post by oldfred on 2009-10-12
Windows is the only system that requires the boot flag. Well some others may but not ubuntu.

You can also move the windows stanzas above the automagic line and leave the default to 0. In your menu.lst find these lines:
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
[COLOR=DarkRed]Put windows stanzas here[/COLOR]
### BEGIN AUTOMAGIC KERNELS LIST

If you update to a new kernel the number of windows stanza at the end will change and your default will change. Everything in the automagic area also gets rewritten, so that is why windows must be before or after the automagic area.

You can also modify the howmany line so when it adds new kernels it will only add so many. change(#) line.
#howmany=2

---

### Post by quixote on 2009-10-12
Hey, you're lucky. :D  The fact that Windows boots means you didn't run into the most common problem with a post-Ubuntu Windows install.

If you manually select the ubuntu boot choice, will it boot it?  

If yes, then all you need to do is get the default pointing to the right entry.  It sounds like windows is the first.  If the current Ubuntu is the second, then it should be "default=1".

If no, then the Ubuntu entry in menu.lst is not pointing to the right partition.  If your Ubuntu is on the second partition of your main hard drive, for instance, grub sees that as (hd0,1).  If it's on the first partition, it would be (hd0,0).  And so on.

One thing: you really shouldn't be getting fsck (filesystem check) errors.  If they don't go away after grub is sorted out, that's not good.  I know it sounds like a huge bother, but the smartest thing to do then is usually to backup the data you need to another drive or partition, and just do a clean install.  It's worth it because fsck errors can lead to data loss.

---

### Post by babygenius55 on 2009-10-13
Thanks for the info folks, I will try. For now I'm just doing what I need to do with a live cd while I do the FSCK with gparted. It goes a lot faster. It has something to do with windows, I took it out of the choices and it stopped happening. I also have KDE as a second choice DM, but I don't see how that makes any difference.I'll post a few pics in a few days or so, I'm not in any huge hurry.

---

### Post by babygenius55 on 2009-10-15
Well, since I don't have much anything I can't afford to lose I'm just going to back up some few things, then format the entire disk, then scan for bad blocks. It's sounds like that's what the problem is.

---

