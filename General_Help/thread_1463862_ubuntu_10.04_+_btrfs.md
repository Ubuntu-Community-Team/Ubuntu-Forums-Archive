---
title: "ubuntu 10.04 + btrfs?"
date: 2010-04-27
forum: General Help
---

### Post by jalyst on 2010-04-27
I'm thinking of doing a minimal ubuntu 10.04 install and then gradually adding the components I want...

It is for a HTPC/PVR/et al machine I'm building....

I'm just wanting to hear people opinions as to whether btrfs is fairly stable enough now for this sort of thing, or is it a waste of my time?

Is ubuntu planning something like this?
[https://fedoraproject.org/wiki/Features/SystemRollbackWithBtrfs](https://fedoraproject.org/wiki/Features/SystemRollbackWithBtrfs)

Thank-you.

---

### Post by psusi on 2010-04-27
No, it isn't anywhere near stable yet.

---

### Post by ibuclaw on 2010-04-27
Stable for Production? Probably not - you'll hit one or two hiccups frequently.

Stable for Testing? Absolutely. :)
Feel free to see my Guide for Karmic here: [http://ubuntuforums.org/showthread.php?t=1389279](http://ubuntuforums.org/showthread.php?t=1389279)

Steps are pretty much identical in Lucid (except that you don't need to add my ppa).

Any questions about oddities, just ask, as will probably already know what they are & have a workaround.

Regards

---

### Post by jalyst on 2010-04-27
Thanks ubuclaw for your detailed feedback,

Not for production, but i still want a reliable htpc/pvr, where content isn't occasionally going to go missing etc.
Can you please elaborate upon "one or two hiccups frequently"?

---

### Post by ibuclaw on 2010-04-28
> **jalyst said:**
> Thanks ubuclaw for your detailed feedback,

Not for production, but i still want a reliable htpc/pvr, where content isn't occasionally going to go missing etc.
Can you please elaborate upon "one or two hiccups frequently"?

Two examples:
1) Upgrades of udev tend to leave it in an unconfigured state (so it needs reinstallation either before you reboot or from a liveCD).
2) GTK Theming and GConf keys mysteriously go missing, even though booting into a snapshot works OK, and running a diff between the two renders nothing (relevant). However running:
```

sudo gconf-schemas --register-all
sudo update-gconf-defaults

```
Seems to fix it.

Due to the weirdness of issue#2 - may be to do with the Debian package manager itself, as is practically unheard of in other distributions.

---

### Post by jalyst on 2010-04-28
Hmm thanks, neither sound like "show-stoppers"...

So long as the advantages outweigh the regular minor glitches (assuming they're always minor!)... 
Then I don't see why I shouldn't chose it as my default fs?

I suppose if one is using it, one doesn't need to fiddle with stuff like LVM any more too?

---

### Post by ibuclaw on 2010-04-28
> **jalyst said:**
> Hmm thanks, neither sound like "show-stoppers"...

So long as the advantages outweigh the regular minor glitches (assuming they're always minor!)... 
Then I don't see why I shouldn't chose it as my default fs?

I suppose if one is using it, one doesn't need to fiddle with stuff like LVM any more too?

Btrfs covers both RAID and LVM-like functionality - although administering it is not quite the same as using mdadm or lvm themselves.

ie: Yes you can have one filesystem that spans multiple devices, and you can add/remove devices on the fly. No you do not have control over the size of the subvolumes unless you decide to go with having filesystems residing in files - in that case you can use truncate to shrink the image and fallocate (or truncate if you want it sparse) to extend it.

(edit): For the time being, I'd also recommend sticking to a separate /home partition that is formatted in the trusty ext3 or ext4 file system.

Regards

---

### Post by jalyst on 2010-04-28
Good suggestion RE home partition, thank-you!
I've heard btrfs has better qualities for SSD's, is that entirely true?
My system volume will be an Intel X25-V 40GB SSD... 
It will house my custom Ubuntu install, and a light Win7 install.

---

### Post by jalyst on 2010-04-28
Thank-you for those extra insights,
Do you still prefer other forms of softRAID and LVM for certain usage scenarios, _instead_ of BTRFS?

> **ibuclaw said:**
> Btrfs covers both RAID and LVM-like functionality - although administering it is not quite the same as using mdadm or lvm themselves.

ie: Yes you can have one filesystem that spans multiple devices, and you can add/remove devices on the fly. No you do not have control over the size of the subvolumes unless you decide to go with having filesystems residing in files - in that case you can use truncate to shrink the image and fallocate (or truncate if you want it sparse) to extend it.

(edit): For the time being, I'd also recommend sticking to a separate /home partition that is formatted in the trusty ext3 or ext4 file system.

Regards

---

### Post by ibuclaw on 2010-04-28
> **jalyst said:**
> Thank-you for those extra insights,
Do you still prefer other forms of softRAID and LVM for certain usage scenarios, _instead_ of BTRFS?

I've never tried Software RAID before, only a Btrfs system spread across two devices. And apart from taking a small while in figuring out what to do in the ramdisk scripts (before the root filesystem has mounted) - have had no extra issues with managing / handling.

The positive I'd say to LVM's though are that you know where everything is in an LVM, and you can have it encrypted.

On the other hand, creating and deleting snapshots in btrfs is substantially faster - as in it takes seconds, not hours.

---

### Post by jalyst on 2010-04-28
> **ibuclaw said:**
> I've never tried Software RAID before, only a Btrfs system spread across two devices. And apart from taking a small while in figuring out what to do in the ramdisk scripts (before the root filesystem has mounted) - have had no extra issues with managing / handling.

If I go the softRAID route later, I'm not locked (I assume) into using BTRFS's built-in RAID. 
So I guess how good/bad it is (for my requirements) compared to other options is irrelevant for now?

> The positive I'd say to LVM's though are that you know where everything is in an LVM,

Not quite sure what you mean by this?
And BTRFS offers no encryption?

> On the other hand, creating and deleting snapshots in btrfs is substantially faster - as in it takes seconds, not hours.

Interesting to know, thanks!

I think you've given me the guts to bypass the default install of ext4, except for /home. 
Thanks for all your input thus far!

---

### Post by jalyst on 2010-04-28
any comments on this? thanks/night.

> **jalyst said:**
> Good suggestion RE home partition, thank-you!
I've heard btrfs has better qualities for SSD's, is that entirely true?
My system volume will be an Intel X25-V 40GB SSD... 
It will house my custom Ubuntu install, and a light Win7 install.

---

### Post by jalyst on 2010-05-22
@ibuclaw/anyone
Could you please help me with the last few questions in #11 & #12?

Thank-you!

---

### Post by madjr on 2010-05-22
> **jalyst said:**
> I'm thinking of doing a minimal ubuntu 10.04 install and then gradually adding the components I want...

It is for a HTPC/PVR/et al machine I'm building....

I'm just wanting to hear people opinions as to whether btrfs is fairly stable enough now for this sort of thing, or is it a waste of my time?

Is ubuntu planning something like this?
[https://fedoraproject.org/wiki/Features/SystemRollbackWithBtrfs](https://fedoraproject.org/wiki/Features/SystemRollbackWithBtrfs)

Thank-you.


testing it in fedora
[http://www.phoronix.com/scan.php?page=article&item=fedora_13_btrfs&num=1](http://www.phoronix.com/scan.php?page=article&item=fedora_13_btrfs&num=1)


might be default in ubuntu
[http://www.phoronix.com/scan.php?page=news_item&px=ODI1Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODI1Mg)


but i think they should work with fedora on this first, if everything in fedora 14 (grub integration and auto snapshots) is good then include it in 11.04

really excited about this, linux will move a big step forward and testing/dev can be twice as fast as if things break you just reboot to a good snapshot

noob-proof too, support can reduced by a lot

---

### Post by jalyst on 2010-05-22
Even if it doesn't come out for a while there's apps like clonezilla for those living on the "bleeding edge" :) 
But I agree, it'd be nice to have that functionality built-in.

Are you able to answer my questions in posts #11 & #12?

---

### Post by madjr on 2010-05-23
> **jalyst said:**
> Even if it doesn't come out for a while there's apps like clonezilla for those living on the "bleeding edge" :) 
But I agree, it'd be nice to have that functionality built-in.

Are you able to answer my questions in posts #11 & #12?

might find some info here:
[http://www.phoronix.com/scan.php?page=search&q=Btrfs](http://www.phoronix.com/scan.php?page=search&q=Btrfs)

---

### Post by jalyst on 2010-05-23
Nothing uufnortnately :( Thanks anyway!

---

### Post by ibuclaw on 2010-05-23
> **jalyst said:**
> @ibuclaw/anyone
Could you please help me with the last few questions in #11 & #12?

Thank-you!
Hi. :)

> **jalyst said:**
> If I go the softRAID route later, I'm not locked (I assume) into using BTRFS's built-in RAID. 
So I guess how good/bad it is (for my requirements) compared to other options is irrelevant for now?

If you switch from Btrfs to SoftRAID, you can't escape the fact that you need to reformat the disks in order to switch. It depends how you see "locked" as. If you have 200GBs of data on a Btrfs system, and have nothing to back it up on, you are kinda "locked", there, aren't you? ;)

If you are wanting a testing system, go Btrfs, else just keep on the stable route, and use the tried and tested filesystems/raid interfaces.

> 
Not quite sure what you mean by this?
And BTRFS offers no encryption?

Ignore me, this is no longer the case. Btrfs recently implemented an ioctl to list all the subvolumes on the filesystem. Infact, there are lots of new nice touches that have gone into the latest release, including a new control command.
See here for updates in 2.6.34: [http://kernelnewbies.org/Linux_2_6_34#head-e677b459b5bd3792f1bfad6a83f8b1ad134c9d77](http://kernelnewbies.org/Linux_2_6_34#head-e677b459b5bd3792f1bfad6a83f8b1ad134c9d77)

@Encryption, Btrfs does not have support for it, but it has [been planned]("http://www.linuxfoundation.org/news-media/blogs/browse/2009/06/conversation-chris-mason-btrfs-next-generation-file-system-linux"), probably as a (very) long term goal.

> **jalyst said:**
> any comments on this? thanks/night.
Btrfs offers a mount -o ssd option, how good that is on ssd's I do not know through personal usage, however phoronix did a test on this about a year ago:
[http://www.phoronix.com/scan.php?page=article&item=btrfs_ssd_mode&num=1](http://www.phoronix.com/scan.php?page=article&item=btrfs_ssd_mode&num=1)


Regards

---

### Post by jalyst on 2010-05-24
> **ibuclaw said:**
> Hi. :)
If you switch from Btrfs to SoftRAID, you can't escape the fact that you need to reformat the disks in order to switch. It depends how you see "locked" as. If you have 200GBs of data on a Btrfs system, and have nothing to back it up on, you are kinda "locked", there, aren't you? ;)

No by "locked" I meant if I use BTRFS it's not _imperative_ that I use it's built-in RAID abilities. 
I can determine which softRAID is best for my needs, & if it's not BTRFS that won't be an issue, right?

> If you are wanting a testing system, go Btrfs, else just keep on the stable route, and use the tried and tested filesystems/raid interfaces.

Yeah I'll most likely use ext4 for this build... 
But I'll probably run a parallel system in a VM that uses BTRFS, just so I can gauge it's viability over time.

Unless you can think of a better approach?

---

### Post by ibuclaw on 2010-05-25
> **jalyst said:**
> No by "locked" I meant if I use BTRFS it's not _imperative_ that I use it's built-in RAID abilities. 
I can determine which softRAID is best for my needs & if it' not BTRFS, that won't be an issue, right?

Oh I see, no you are not locked then. :)

Infact, you can specify how you want data and metadata to be spanned across the device(s) using the **-d** and **-m** flags at creation time with the mkfs.btrfs command. Valid options being: raid0, raid1, raid10 and single. Should be self explanatory what each mean.


> 
Yeah I'll most likely use ext4 for this build... 
But I'll probably run a parallel system in a VM that uses BTRFS, just so I can gauge it.s viability over time.

Unless you can think of a better approach?
Sounds like a safe plan to me. ;)

Regards

---

### Post by jalyst on 2010-05-25
Actually I think I'll use ext4 for /home and maybe one or two other subdirs, but will use BTRFS for the rest.
Hopefully having a mixture like that won't cause issues later when I want to fiddle with volume managers & softRAID!?

---

