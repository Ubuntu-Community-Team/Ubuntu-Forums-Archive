---
title: "Dumb &quot;How to&quot; question."
date: 2012-04-23
forum: General Help
---

### Post by mugwump40 on 2012-04-23
I have UBUNTU 8.04 working the way I want it to, and I am wondering how to back up the ENTIRE hard drive in case I have a crash or whatever.  I'm thinking of a tool like Norton Ghost (which I don't have or use).  In case of a real bomb out, I just want to reload the entire system and be back running without having to reload all the optional programs, etc.  I am currently using 17.5 GB on my drive.  I could buy a 32 GB USB plug in drive or use DVD's or another hard drive.  Suggestions????

---

### Post by r-senior on 2012-04-23
Sounds like you are looking for Clonezilla ...

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by NTL2009 on 2012-04-25
One problem you may run into with Clonezilla:

> The destination partition must be equal or larger than the source one.

You mentioned that you are using  17.5 GB  on your drive, but I assume the drive itself is much larger than that. You'll need an external as large as your entire partition.

You could look at this thread, but there are a number of steps required to get it bootable, and I have not got my head around all the details.

[http://ubuntuforums.org/showthread.php?p=11869785#post11869785](http://ubuntuforums.org/showthread.php?p=11869785#post11869785)

-NTL2009

---

### Post by holycow131415 on 2012-04-25
remastersys is good as well.

---

### Post by techsupport on 2012-04-25
> **holycow131415 said:**
> remastersys is good as well.

I recommend Remastersys:

[http://debianhelp.wordpress.com/2012/04/20/how-to-install-and-use-remastersys-in-ubuntu-os/](http://debianhelp.wordpress.com/2012/04/20/how-to-install-and-use-remastersys-in-ubuntu-os/)

:guitar:

---

### Post by Gatorade on 2012-04-25
> **techsupport said:**
> I recommend Remastersys:

[http://debianhelp.wordpress.com/2012/04/20/how-to-install-and-use-remastersys-in-ubuntu-os/](http://debianhelp.wordpress.com/2012/04/20/how-to-install-and-use-remastersys-in-ubuntu-os/)

:guitar:

what if you have a 500GB hard drive , do you need a 500Gb drive to back up even if its not full?
or what about a dual boot system ? does it clone everything on the drive or just the linux partition?

---

### Post by techsupport on 2012-04-25
> **Gatorade said:**
> what if you have a 500GB hard drive , do you need a 500Gb drive to back up even if its not full?
or what about a dual boot system ? does it clone everything on the drive or just the linux partition?

No, you are thinking of Clonezilla. 

Remastersys creates a custom Ubuntu OS based on your existing Ubuntu OS installed system.

Migrate your home data to an external device if you are going to use BACKUP mode.

---

### Post by NTL2009 on 2012-04-25
> **holycow131415 said:**
> remastersys is good as well.

Some limitations for many of us (including the OP, with 17.5GB install):

> Keep in mind that currently there is a size limitation set at 4GB, which means your entire compressed filesystem.squashfs file, your complete compressed system, must be less than 4GB, otherwise it will not work.

-NTL2009

---

### Post by techsupport on 2012-04-25
> **NTL2009 said:**
> Some limitations for many of us (including the OP, with 17.5GB install):



-NTL2009

Use Clonezilla instead?

---

### Post by Gatorade on 2012-04-25
> **techsupport said:**
> No, you are thinking of Clonezilla. 

Remastersys creates a custom Ubuntu OS based on your existing Ubuntu OS installed system.

Migrate your home data to an external device if you are going to use BACKUP mode.

 will this work the exact same for Mint since mint is based on Ubuntu?

---

### Post by techsupport on 2012-04-25
> **Gatorade said:**
> will this work the exact same for Mint since mint is based on Ubuntu?

Mint used the older version Remastersys on the old versions of Mint. 

Last time I checked I think they have their own variant of Remastersys now. But you would want to post that question to the Mint forums to be sure about that.

---

### Post by Gatorade on 2012-04-26
ok.

---

### Post by NTL2009 on 2012-04-26
So **Remastersys** has the 4GB limit, and **Clonezilla** requires a destination partition as large as the source partition (even if only a small % is actually used).

Is there something w/o these limits? Can the OP clone his 17.5GB system (which is likely on a 160GB or larger disk) to a 32GB partition, and preferably boot right from that so he could test it out? That way, he knows it works w/o going through a re-install (if it fails then, you are hosed any way). 

-NTL2009

---

### Post by Fragadelic on 2012-04-26
I am the remastersys developer.

The 4GB limit isn't dictated by remastersys directly.  It is a limitation imposed by genisoimage which is the tool to create the iso file.  The limitation is due to the fact that it won't allow any single file to be larger that 4GB on the iso.  The Ubuntu live system must be contained in a single filesystem.squashfs file since this is also required by the Ubiquity installer in order to install it back.

2 things are at play here:

1 - genisoimage won't allow a file larger than 4GB to be on the iso.

2 - Ubiquity ans casper require the entire live system to be in a single filesystem.squashfs file.

I've been thinking of ways to get around this.  I have been able to modify casper to allow multiple squashfs files and it works but install will fail as Ubiquity only looks at a single aufs mount point.  I haven't had time to discuss this with Colin Watson but I do plan to.  I'll need to provide the code changes to Colin so it can be included in the official packages but I haven't gotten that far yet.

I'm just finishing up with the remastersys version that fully supports Ubuntu 12.04.

---

### Post by Trapper on 2012-04-26
> **NTL2009 said:**
> So **Remastersys** has the 4GB limit

All this takes into account that it's a single user system and all personal stuff is in your home folder. Strategy will vary, otherwise:

Don't let the 4GB limit scare you. All you personal stuff (entire home folder ... including all hidden folders/files) should be manually backed up _separately_. Remastersys in backup mode (and with the instruction to not back up anything in your home folder) will provide you with a duplicate installable image of your current system.  After you install it to your new computer/drive/partition you simply copy in your complete home folder that you backed up. Presto ... you have a duplicate of your original system.


Make sure you use a remastersys version that is compatible with your version of ubuntu.

---

### Post by Trapper on 2012-04-26
> **Fragadelic said:**
> I am the remastersys developer.

<<< snipped >>>

I'm just finishing up with the remastersys version that fully supports Ubuntu 12.04.

I am anxiously awaiting the 12.04 version. I'm running MATE DE on 12.04 and want to see how well remastersys works in that scenario for both a backup and distribution.

---

### Post by NTL2009 on 2012-04-26
Thanks for the replies **Trapper** and **Fragadelic** (esp great to get info right from the developer!).

Remastersys sounds like a great tool, and I know a lot of people use it and it's good to see the developer is continuing to improve it. I'll go ahead and give it a try to back up my current system. I do have '/home' on a separate partition, so I can copy or rsync that separately (I guess during an install, you first re-copy '/home', then point the installer to that '/home' partition w/o formatting it). 

My '/' is 6.2GB, so I'm not sure that would compress down to < 4GB. Also, can I have Remastersys copy the files to an external HDD partition? I only see refs to CD/DVD and flash drives.

That said, I don't think Remastersys is the ideal tool for straight system backups (but sounds fantastic for making installation disks). The reasons I say this are that I'd like to back my system up to a partition uncompressed, that only needs to be large enough to hold my 'used' space, and be able to boot from it right after I copy. This way, one could verify the backup w/o going through the extra step of re-installing it, which is time consuming, and requires another partition if you don't want to write over your original (and I don't, unless it actually crashed).

So far, all the steps I've seen for making the backup bootable involve editing fstab and some other grub work, and I have yet to get my head around all the specifics steps involved in that.

-NTL2009

---

### Post by mugwump40 on 2012-04-27
Thanks for the tips.  I've downloaded Clonezilla and now I'm going to purchase a bigger  thumb drive.  I'll probably have to resize the partition to be able to back it up.  Can't find/afford :-( a thumb drive big enough to back up the whole HD.  I have other HD's I could use, but like the portability of a USB thumb drive.

---

