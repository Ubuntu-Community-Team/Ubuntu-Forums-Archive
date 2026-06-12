---
title: "Dual boot Win/Linux, RAID1.  I HAD it, it broke, can't FIX it!"
date: 2012-04-15
forum: General Help
---

### Post by ladasky on 2012-04-15
Oh, I am so ready to start swearing now.

I keep Windows around for just one reason: tax preparation here in the United States.  No tax preparation software runs on Wine.

Yes, I know that some companies offer tax preparation software on-line.  I am not ready to trust my deadline-driven preparations, or my many cycles of revisions, as I read through the interview questions and IRS documents, to an Internet connection.  I want tax software which runs entirely locally, right up to the moment I am ready to file.  And if my network connection should happen to choke at that critical moment, I can always print my return to paper, and go to the post office.

Trundling papers back and forth between my son's Windows gaming computer and my Linux machine last year was its own special hassle.  So, a few months ago, I bit the bullet, and converted my system to dual-boot.  My system was already running a software-based RAID1.

I got my son's old copy of Vista.  My finished system boasted a functioning RAID1, too, using the motherboard's built-in RAID (which Windows seems to require, but which Linux can do without).  Of course, greedy Windows clobbered my Ubuntu installation :mad:, and I had to re-install Ubuntu again.  But I was pretty proud my myself for getting it to work.  

(FYI, the motherboard is a Gigabyte GA-MA78GM-US2H, vintage 2009.  Not too old.  And as you can see from my profile information, I'm using Oneiric.)

Well, three days ago, my RAID made a nasty announcement during boot-up: "Critical failure: a disk member of an array has failed or is not responding."  ***Caramba***.  I got through to a GRUB page anyway.  I discovered that Linux would hang repeatedly for 10-15 seconds at a time if I booted into it.  I could barely make selections with the mouse, which also froze.  Even the System Monitor would seize up, though the CPU wouldn't spike at all during a freeze.  A very unsettling set of symptoms.  Windows, strangely, was soldiering on.  

I quickly booted into Oneiric from an external drive, where it ran just fine.  I backed up all of my data (Linux and Windows), de-configured my RAID, and booted exclusively into Windows for the next few days to make sure I finished my taxes on time.  

I didn't know which of my two hard drives I was booting from.  Eventually, I tried unplugging each of them in turn.  They both seemed to boot Windows fine, and both of them read data from their Linux partitions without errors.  I have a feeling that my two drives were just out of sync.  Nothing appears to have actually failed.

Today, I set about trying to rebuild my RAID1.  I couldn't get an automatic mirroring process to start just by re-connecting the two drives into a RAID.  I was under the impression that this was how RAID was supposed to work?  Oh well, I guess that RAID1 couldn't possibly know which of the two drives had the problem.

So I decided I would just start from scratch.  I booted into Linux from my external drive, deleted the partition table from the RAID, and made a new one.  I then booted the Vista CD.  As instructed, I installed the motherboard's Windows RAID driver.  The first cycle of the installation finished, and then the computer said it would reboot.  OK.  So far, so good.

But on reboot, the boot loader passed right by the opportunity to boot from the RAID, and simply hung, with the message "Press any key to boot from CD or DVD....." at the bottom of the screen.  I tried a reboot, pressed F12, and forced the selection of "Hard Disk".  This yielded the message "A disk error occurred.  Press Ctrl-Alt-Del to restart."  And if I did that?  My RAID went back to reporting "Critical failure: a disk member of an array has failed or is not responding." ](*,) 

Until the "critical error" message reappears, Linux knows that I have two drives, and is ready to mount the various partitions on them in tandem as /dev/mapper/...  Linux will also mount any partition that I want from each physical drive separately, as /dev/sda... or /dev/sdb...

I swear I've done everything the same way that I did the last time, just as my motherboard manual described.  Windows wouldn't know it.  Before you ask, Windows support pages are not very helpful on these matters.  I have found some web pages that suggest that the SB700 ROM-based RAID controllers on AMD motherboards "get lobotomized" after a while.  The implication is that native RAID **simply stops working** after a while on these boards?  But that otherwise, everything is still functional?  That's psychotic.

The ONLY thing I can imagine that I did that was different was by not having a Linux installation for Windows to undo during its own installation.  I refuse to examine that possibility.  I'm trying to install Vista to a clean RAID, and thus deprive it of the enjoyment of wasting my time.  Maybe it wants to take revenge on me.  

Anyone still with me?  I know, I'm going on.  Thanks for sticking with this story.

Now, while I started by trying to put things back the way that they were, I am considering alternatives.  What I really need is a frequently-updated mirror of my data, in both operating systems.  RAID is, theoretically, exactly that.  But after my RAID1 broke, and I don't actually see anything wrong with either of my hard drives, I'm beginning to question how good RAID really is.  At least, RAID1.

Now, Linux can mount an NTFS partition.  Is there a way I can use mdadm, or rsync, to mirror the Windows stuff?  It would be nice if that mirror was also **bootable**, but I would settle for an NTFS partition to which I could simply apply a Windows "repair" to get running if I had to.

OK, now I'm truly done.  Thanks for reading, and any advice you may have.

---

