---
title: "Matters Related to HDs And Partitions"
date: 2010-07-16
forum: General Help
---

### Post by oldefoxx on 2010-07-16
I learned something tonight that had never crossed my mind before.  I don't even know if the writers of the various emails I learned it from really understood it.  And I don't know the extent of what I learned either.

Here is what it came down to.  I've been fighting an uphill battle to get Ubuntu or Fedora onto a desktop and have either boot up, or recognise other
installed OSes on other partitions as they should.  I finally got down to where I could do an install, but on bootup, grub old report either an Error 17 or Error 22. I kept searching for answers, and trying different possible solutions, but no real progress.  I finally reformatted the three hard drives installed, and began over.  That is when I started getting the Error 22s in place of the previous Error 17s.

You know what I found these both mean?  That grub could not find a given partition.  Get that?  Somehow grub was looking for a partition that probably dated back much earlier in my efforts, and no effort to to start over on a given drive with new partition tables, or reformat, or to install Ubuntu or work with grub was making any difference.  It wanted that partition back where it was and as it was, and with my years of experience, I could not even begin to figure out how that could be.

It turns out, from what I've read and tried, that this is someting that can happen with the hard drive's MBR, or Master Boot Record.  See, when hackers found ways to get viruses on PCs from floppy disks and all, one favorate attack point was the boot record, which is what needs to be called to get your system up and running.  The fight-back from Microsoft was the MBR, which you might think of as the Master copy of the Boot Record.   Varous techniques came into existence for taking the MBR and copying over the boot record to help undo the effects of an attack.


to help protect the MBR from attack, very little information was put out about it.  It just became accepted that if the MBR was still intact, you should be able to get that PC to boot again.  But software moves on, even the boot process, so there had to be a way to update what was stored in the MBR record as well.  Thus, the FDISK command was adapted to take the current systems files, the two basic ones, and set those as part of the MBR when you executed FDISK /MBR.

There is no specific limitations on the MBR in terms of length or whatever.  And it seems that it can become somewhat cluttered, where portions of the previous MBR still remain behind a new one, or possibly the new one is used to extend the present one.  If you generate a new partition table, that does not erradicate what is on the hard drive already, it just removes the structure that lets you get to it on demand.
So there might be a possibility that lost data or programs could become part of an extended MBR in some cases

If any of these things happen, then Grub can indeed report errors because none of what it has store really applies any more, or at least not in this context.  So what to do about it?

Some just say get a Windows XP Setup disk and use what is on it, because this is a byprduct of their invention.  But not everyone has access to a Windows XP Setup disk.  Besides, others reason that there has to be some way to get a Linux distro to do as well.

Maybe so, but it is not always apparent when it needs being done.  And in tring to find a Linux way,  I found out that several suggested methods cannot be directly downloaded and installed under Ubuntu.  One was named fixmbr, but it is not available through the Ubuntu repositories and could not be found at the original link either.  Two methods suggested that you could do it with grub, and I got one of those methods to work, but it did not fix the problem.  Acouple of other methods said that you could use install-mbr, but there was nothing given as to where or how to get my hands on instqll-mbr.

Some more searching, and I found that install-mbr is just part of a package named mbr,  and that is available.  It turns out that install_mbr needs am arggument, either the drive or a specific partition, and does te comman, but that is it.  No indication of what it did or if it succeeded somehow with fiing the problem.

Maybe it did.   Instead of a normal grub error message, it slowly put the letters MBR NF: at the upper left corner of the screen.  To me, that might stand for Master Boot Recprd Not Found:, but who can be sure?

I guess my next step will be to try and install Ubuntu 9.04 on the first partition again, then seen what happens with the MBR after that.  But it ia late, I need to get to bed, and so I decided on a write-up here, then a renewed effort again tomorrow.

You know, it bugs me that gparted and partiton editor offer nothing for dealing with the mbr.  And my last go-around with gparted with the three drives was getting a persistent error everytime I tried to format the third partition on the second drive.  I kept trying to adjust the size of the first two partitions, thinking the presence of a bad place on the hard drive did not mean I had to give up what useful space still remaieed.

But the shoker was that on th final go-around, it turned out that it might not be a bad spot on the hard drive, but a limition of gparted where it could not handle the additon of another partition internally.

So what's the story?  I think some discussion here might clear matters up to some extent.  And I can now see that matters involving both the partition table and mbr could have resulted in some of my initial problems with both 9.10 and 10.04.  Now it bothers me that the install process does not strive to counter problems that can occur in these two areas, because I knew nothing of these matters, even with many years of experience, and I don't know of anyone who might have.

---

### Post by dcstar on 2010-07-16
> **oldefoxx said:**
> I learned something tonight that had never crossed my mind before.
........

I didn't, can you please edit your rants and post some specific issues that need attention?

---

### Post by robsoles on 2010-07-16
I've the impression that palimpsest (in 10.04 GUI: "System"->"Administration"->"Disk Utility") nukes the existing MBR if you go far enough, ie delete each partition and keep choosing delete options till not offered things to delete anymore and then work your way in from there. (Just going by memory, I don't have a drive I care to delete on me right now!)

It is accessible from a LiveCD.

If anyone can tell me my impressions are wrong (or maybe even right) and fill my head with facts about this I'd be delighted.

---

### Post by QLee on 2010-07-16
[QUOTE=oldefoxx]
There is no specific limitations on the MBR in terms of length or whatever. [/QUOTE]

Well, there is, it's the 512 bytes beginning at the first sector of the first head at the first cylinder on a physical drive. That's what is going to be meant by MBR when you see it written. This does not negate any aspects of the modern extensions GPT/EFI.

[QUOTE=oldefoxx]And it seems that it can become somewhat cluttered, where portions of the previous MBR still remain behind a new one, or possibly the new one is used to extend the present one.  [/QUOTE]

You must have misunderstood whatever you read, there isn't any "cluttering", portions don't "remain behind" (Although, people do forget to update GRUB after they have made a change to the system. For example, when they choose to reformat a partition, thus changing UUID, this happens with a re-install too.) When you write the MBR portion of GRUB to the MBR it overwrites the old MBR data.


[QUOTE=oldefoxx]So what's the story?  I think some discussion here might clear matters up to some extent. [/QUOTE]

Good question, what is the story. You haven't asked any clear questions, so I don't know what you want to discuss. Since you mention 9.04, maybe you'd consider upgrading to a newer version.

---

### Post by gzarkadas on 2010-07-16
Gparted supports writing the MBR (Menu `Device|Create Partition Teable').  It is just that this actions wipes all the partitions. Check first if the BIOS has on an option to protect MBR (maybe hidden under an `antivirus' or `guard' wording); if yes you 'll have to disable it.

Note that it is better to break multiple partition operations in small sets; I had too some failures with gparted that were fixed when I repeated the process but broke it down to successive, smaller sets of operations.

The MBR is documented; see for example this [Wikipedia entry]("http://en.wikipedia.org/wiki/Master_boot_record"). 

You can use `dd' to copy the mbr to a file and then `bless' to study it versus the table and info contained in the link above. The example below assumes your disk is in /dev/sda; modify it if is somewhere else.

```

sudo dd if=/dev/sda of=/root/mbr-copy count=1
sudo bless /root/mbr-copy

```The `mbr' package as stated in [Boot Process page of the Debian Wiki]("http://wiki.debian.org/BootProcess") (see the table under Boot Process heading) uses a different bootloader than grub. If you used it to write to the MBR, then you probably messed up with Grub. If this is the case try to reinstall grub. Here are some documentation links:

Grub (Legacy) - for Ubuntu 9.04 and before: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
Grub2 - for Ubuntu 9.10 and later: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

For something more specialised, you will have to make your description more detailed; less story, more facts (though I do understand that late-night troubles, as your intro implies, do tend to produce long and emotional texts :)).

---

