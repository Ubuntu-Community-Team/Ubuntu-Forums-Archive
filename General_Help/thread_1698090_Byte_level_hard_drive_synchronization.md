---
title: "Byte level hard drive synchronization?"
date: 2011-03-01
forum: General Help
---

### Post by jordanmoore on 2011-03-01
Hey everyone,

I'm looking for a tool for Linux (I use ubuntu on a usb stick) that can perform byte level synchronization of a hard drive.

What I wish to do is backup the entire (internal) hard drive onto an external hard drive, to ensure I can access all the files I'm using ubuntu booted from a usb stick.
(The internal hard drive has windows 7 installed)

Preferably this tool should have an easy to use GUI because I'm not great with the terminal, and my backups will be done late at night when I just want to get to bed - not mess around with a terminal.

Does anyone have any suggestions for me?

Thanks, Jordan


Note: I don't have the external hard drive yet, I'm researching tools first.

---

### Post by srs5694 on 2011-03-01
```

sudo dd if=/dev/sda of=/dev/sdb

```

This does a byte-level copy from /dev/sda to /dev/sdb. It will take a long time to execute, and you won't need to interact with it. The target disk must be as large as or larger than the original. It's also *imperative* that you get the if= and of= options right; reversing them will wipe out your original disk! (Similar comments would apply to any tool to do what you're asking.)

---

### Post by Hedgehog1 on 2011-03-01
jordanmoore,

Fellow ***Ubuntu-On-A-Stick*** user!

The next step up from the (perfectly functionality) **dd** command is **ddrescue** command.  It has two extra features: (1) works around bad sectors on the 'source' hard drive & (2) it has an option to be able to pick up where it left off.

But both will work.

You can create a script on your ***Ubuntu-On-A-Stick*** (the worlds only ***True Pocket PC!***) to make running it as easy as possible.

***The Hedge***

:KS

*p.s. Did you know hedgehogs have no pockets?!?*

---

### Post by jordanmoore on 2011-03-02
Thank you very much for these answers, I'll try out both of the commands on USB sticks to see how they work :)

Three Quick questions however:
[LIST]
[*]After the first initial backup (which will take a long time), will following backups be fast?
[*]If I delete a file on the internal HDD, will it delete on the external HDD?
[*]My internal HDD is fully encrypted using "TrueCrypt", will this command still work?
[/LIST]

Many Thanks

---

### Post by matt_symes on 2011-03-02
Hi

> Three Quick questions however:
After the first initial backup (which will take a long time), will following backups be fast?


With dd; no. It will copy the entire hard drive byte by byte each time. Unsure about ddrescue but i imagine it will work the same way.

> If I delete a file on the internal HDD, will it delete on the external HDD?

Yes but for the above reason. It will copy the whole hard drive.

> My internal HDD is fully encrypted using "TrueCrypt", will this command still work?

Yes. They will both still work.

I don't see why you don't use Clonezilla to backup

Kind regards

---

### Post by jordanmoore on 2011-03-02
Thanks for answering my questions so swiftly, I appreciate it.

It would appear that the "dd" command is not what I'm looking for then, I was hoping to find something that - after the initial backup - only had to backup the changes.

I'll definitely be taking a look at "clonezilla", thanks for that suggestion.

---

### Post by srs5694 on 2011-03-02
Your two criteria -- byte-level synchronization and incremental backups -- are at odds with one another. I don't know of any program that does both, and from a theoretical level, it's impossible to do a byte-level synchronization without at least reading the entire source drive -- there's no way to know if a source byte has changed without reading it.

Note that byte-level synchronization means synchronizing everything at a low level, even space that's not currently in use on the hard disk. There are certainly cases where this is necessary, but I suspect yours might not be one of them. Why do you want to do a byte-level backup?

Personally, I generally use the Linux tar utility for backups. It's not a low-level backup tool, but it does support incremental backups. It's also a text-mode utility, so you might not like it; but there are GUI front-ends to it, such as [TAR GUI.](http://sourceforge.net/projects/targui/) For disk-to-disk backups, you might look into rsync or a GUI front-end to it, such as [Grsync.](http://www.opbyte.it/grsync/)

---

### Post by matt_symes on 2011-03-02
Hi

srs5694 has raised some good points in the post above. Your backup strategy should depend on what you are trying to achieve.

Clonezilla is excellent for backup up partitions and whole drive. This is excellent for disaster recovery if the entire drive fails.

[http://clonezilla.org/](http://clonezilla.org/)

Tar is a command line tool for backing up files that can be very easily scripted. It will back up files and folders to local hard drives but will not back up the mbr and other such areas of the hard drive so cannot be used to restore the entire drive. You can remotely backup using rsync.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

You need to decide your backup strategy.

BTW: I use both Clonezilla and Tar.

Kind regards

---

### Post by jordanmoore on 2011-03-02
I was thinking about byte level synchronization because I was under the impression that this was the fastest method - but my knowledge doesn't lie in this area so it appears I was wrong - thanks for pointing this out.

From what I've read it appears that "clonezilla" is the utility which is going to do what I wish.

The following is the purpose of my backup:
My laptop contains a lot of data which is precious to me, including projects that I work on, software I write, plus my college work. It also has over 30GB of software installed which is inconvenient to re-download on a 300kbps connection.
Within the upcoming months I'm going to begin riding a motorbike to commute to college, and god forbid if I crash I don't want to loose my data.
Essentially I want my backup to make a mirror image of my hard drive; this is so that if I smash the laptop to pieces, I can simply purchase the same laptop again and mirror the backup to the internal hard drive - leaving me with essentially the exact laptop I broke.
I was under the impression that doing a byte level synchronization from a USB Ubuntu stick was the best way to do this - but I'm really just looking for the fastest method to backup my internal hard drive to an external one.

Sorry for any confusion, and once again, thanks for all the help! :)

---

### Post by YesWeCan on 2011-03-02
You won't find an incremental, byte-level backup.
The simplest way is to use sbackup, but check out [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by Hedgehog1 on 2011-03-02
> **jordanmoore said:**
> 
What I wish to do is backup the entire (internal) hard drive onto an external hard drive, to ensure I can access all the files I'm using ubuntu booted from a usb stick.  [SIZE="2"]**(The internal hard drive has windows 7 installed)**[/SIZE]


Folks - remember the OP is backing up a Windows system using his **Ubuntu-On-A-Stick**.

Clonezilla will backup windows, but it is it's own Linux CD (but it works).  dd and dd_rescue do as well.  None of these three options offer incremental backup, as was pointed out.

Are there issues with TAR based backups of NTFS partitions?  I have never tried it.

---

### Post by matt_symes on 2011-03-02
Hi

> Are there issues with TAR based backups of NTFS partitions? I have never tried it.

Tar can be used to backup windows files and folders. There might be issues with filename characters but i have never come across any yet.

Kind regards

---

### Post by srs5694 on 2011-03-02
I missed that this was a Windows installation. If you don't have Linux installed on the computer at all, then I recommend you look to Windows backup tools, not Linux tools. One I've used successfully is [DriveImage XML;](http://www.runtime.org/driveimage-xml.htm) however, my needs for Windows backup are modest. I *have* successfully backed up and restored using this software, though. One caveat: You'll need to prepare a custom Windows recovery CD/DVD to restore using DriveImage XML. Its Web page provides instructions for creating such a disc, but the procedure is a bit hairy.

I doubt if backing up a bootable NTFS partition using tar from Linux would work, since when you mount NTFS in Linux, you lose access to certain types of data, such as NTFS's ownership and permissions data. (There's no easy way to map this data to Linux equivalents, so the Linux drivers ignore it.) There might be a tar port to Windows that would work from Windows, though. This issue might not be a big deal on a data-only partition.

If you absolutely must back up an NTFS partition from Linux, I recommend ntfsbackup, which is in one of the regular Linux NTFS packages (I don't recall which one offhand). It can create backups that omit unused sectors, which can help with speed, particularly if your drive is far from full, and it's a low-level utility that can preserve bootability; however, there's no incremental backup option, and you've got to be *very* careful when restoring to restore only to a partition that starts on the same sector as the original, or it won't boot.

Now, all that said, if the computer dual-boots between Linux and Windows, you can still use a Linux option (tar, rsync, etc.) to back up the Linux partition(s), along with a native Windows tool to back up the Windows partition(s). Something like Clonezilla can theoretically handle both. (I think it uses ntfsbackup to handle NTFS, but I'm not positive of that.)

---

### Post by jordanmoore on 2011-03-04
Learning some very interesting things here.

The reason I wish to choose ubuntu on a stick is because I need access to files that cannot be copied while running windows (like shell32.dll, sam, etc).

I do need a method that can backup the boot sector too because, as my hard drive is encrypted, the first bootloader is actually where I have to enter the decryption key. (though I have a DVD which can restore this boot loader).

My problem is however, I cannot run a windows tool because that would require windows - and I don't "think" I'd be able to fit a bootable windows on a 2GB usb stick.


I read something interesting about setting up a "raid" drive or something. Would this, if setup correctly, essentially act as a backup? (because to my knowledge it's essentially a mirror image).

---

### Post by jerome1232 on 2011-03-04
A RAID mirror is _NOT_ a backup. It's for fault tolerance only. (ie if one drive fails the computer can continue to run normally)

If your Windows partition is encrypted using a Windows specific encryption tool then your only option from linux may be to do a byte-for-byte copy since linux won't be able to unlock the encryption.

---

### Post by jordanmoore on 2011-03-04
The encryption tool is available for linux and mac too. Although I would not like to decrypt the drive at any stage because this would result in an unencrypted backup on the external drive - which would kind of ruin the whole point of encrypting the hard drive in the first place in my opinion.

Can anyone give me an estimated time it would take to do a byte to byte backup using "dd" using a 250GB source drive to a USB external drive (480mpbs connection)? (internal hdd is 5400rpm if that helps).

Thanks again!

---

### Post by jerome1232 on 2011-03-04
If you want to do an incremental type backup you need to unlock the encryption. That doesn't necessarily result in an unencrypted backup, you just encrypt the target backup partition.

---

### Post by jordanmoore on 2011-03-04
You're absoloutly right, that would work. I think I've discovered what I'll need to do now.

My internal HDD is 250GB.
I'll purchase a 320GB external hard drive.
On the external hard drive I'll create two partitions:
[LIST]
[*]backup partition (260GB) for (weekly) byte level backup
[*]backup partition (60GB) for (nightly) backup of most important files
[/LIST]

Thanks for all your help everyone, I truly appreciate it! :)

---

