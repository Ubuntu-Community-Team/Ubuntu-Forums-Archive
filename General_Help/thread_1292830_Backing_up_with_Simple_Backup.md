---
title: "Backing up with Simple Backup"
date: 2009-10-16
forum: General Help
---

### Post by mcedata on 2009-10-16
Hi, need a bit of a nudge here. I've been using Simple Backup for a while, and find it very easy to use. However, I'm not *quite* versed enough in Ubuntu yet to be confident that I'm getting everything in my backups. I run a Windows and a Linux box side-by-side, using a KVM switch to move back and forth. Both hard drives have about the same amount of data in GBs; the Windows backup takes close to an hour (two hours, if I include the "compare" pass. The Linux backup takes about ten minutes. I know Linux is a dynamite OS, but is it that much better than Windows that it can do this kind of magic, or is what I'm seeing the fact that I'm not backing up everything on the Linux box?

I want to do a full backup...everything on the hard drive. In Simple Backup, it asks for the "includes"...the directories I want backed up. Is there a simple way to tell the software to back up the whole nine yards, without having to list every directory I want to save?

Thanks for any help, it's much appreciated.

Steve

---

### Post by TheStroj on 2009-10-16
If you choose to backup '/', you'll backup everything.
Everything is in that directory!

---

### Post by Zill on 2009-10-16
> **mcedata said:**
> ...I want to do a full backup...everything on the hard drive. In Simple Backup, it asks for the "includes"...the directories I want backed up. Is there a simple way to tell the software to back up the whole nine yards, without having to list every directory I want to save?
Do you *really* want to backup the whole hard disk?  This is not a very efficient way of producing backups.  For example, why backup the operating system and all the associated system files when these can easily be reinstalled from the original Ubuntu CD?

Most users find the SBackup defaults are a good choice in that it backs up user date for all /home directories, together with the configuration files in /etc.  This is the most important data to backup and, eventually, restore in the event of a HDD crash.

However, if you really do want to backup *everything* with SBackup then I guess you just need to have "/" (the root directory) in the "include" tab.  Then make sure you have nothing in the "exclude" tab.  (I have not tried this so this advice is offered without warranty!)

Alternatively, you may like to take a look at other "whole disk" backup applications such as [Clonezilla]("http://clonezilla.org/").

---

### Post by mcedata on 2009-10-18
Zill, TheStroj, thanks, that was the info I was looking for. Tried it, and it does what I need it to do.

To answer the question about "do I really want to back up everything"; I'm just a bit new to Ubuntu and am being a bit paranoid about losing stuff should I have a crash.  After all, using Windoze for a bunch of years will make you that way!  I plead Winsanity.<G>

Thanks again,

Steve
<mcedata>

---

### Post by mlnease on 2009-11-01
Hi Zill,

I've been using SBackup for some years now and am happy with it--I've had to do a few restores and they've always gone fine.  What I'm wondering now is, if I save a copy of a backup file to Gspace (on Gmail's server), will it be possible to restore from there in case of a bad crash (one that makes /var inaccessible/unusable?

Thanks in Advance,

mike

---

### Post by Zill on 2009-11-02
mlnease:  I don't believe that SBackup can *directly* restore from a web server.

However, this shouldn't normally be a problem as, in the event of a HDD crash, you will need to reinstall the Ubuntu OS anyway.  This will recreate the file system, including /var.  All you will need to do is to connect to your web server (Gspace) and then download your backup data to its original location on the filesystem.  Then restore using SBackup in the usual way.

BTW, you can save/restore your backups to/from any media you can mount on your filesystem, it doesn't *need* to be the /var directory.  For example, I backup to a directory on another PC, mounted on my local filesystem via NFS.

---

### Post by mlnease on 2009-11-02
HI Zill,

> **Zill said:**
> mlnease:  I don't believe that SBackup can *directly* restore from a web server.

However, this shouldn't normally be a problem as, in the event of a HDD crash, you will need to reinstall the Ubuntu OS anyway.  This will recreate the file system, including /var.  All you will need to do is to connect to your web server (Gspace) and then download your backup data to its original location on the filesystem.  Then restore using SBackup in the usual way.

BTW, you can save/restore your backups to/from any media you can mount on your filesystem, it doesn't *need* to be the /var directory.  For example, I backup to a directory on another PC, mounted on my local filesystem via NFS.

Thanks, this is obvious now you point it out.  I've also backed up onto a UBS thumb drive--I just hadn't yet figured out what you've pointed out above.

Thanks Again,

mike

---

