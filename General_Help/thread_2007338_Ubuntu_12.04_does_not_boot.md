---
title: "Ubuntu 12.04 does not boot"
date: 2012-06-20
forum: General Help
---

### Post by flyingfisch on 2012-06-20
Hi,

My Dad's laptop has been running ubuntu for about 6 months now.

The week after 12.04 came out in April he upgraded. The upgrade was flawless as far as I know.

Anyway, yesterday he was using the laptop and it froze. He did a hard restart and Ubuntu would not boot. It would just show the boot screen infinitely.

We used the ultimate boot CD to fix some bad sectors on the HDD.

After that, Win Vista would boot but ubuntu endlessly does some error messages, and after about an hour, produced this:

```

end_request: I/O error, dev sda, sector 291575976
ata1: EH Complete
init: hash.c:296:Assertion failed in nih_hash_search: hash != NULL
init: Caught abort, core dumped.
Kernel Panic - not syncing: Attempted to kill init!
PID: 1, comm: init not Tainted 3.2.0-24-generic #39 Ubuntu

Call trace:
? printk+0x2d/0x2f
panic+0x5c/0x161
forget_original_parent+0x1e4/0x1f0
? _raw_spin_lock_irqsave+0x2d/0x40
exit_notify+0x14/0x140
do_exit+0x1ac/0x390
? remove_vma+0x44/0x60
do_group_exit+0x38/0xa0
sys_exit_group+0x18/0x20
syscall_call+0x7/0xb

```

Before all the lines there were numbers in brackets which I suppose represent time elapsed.

The lines after "Call Trace" had hex numbers in "<>"s.

Should I reinstall ubuntu or is there a way to fix this?

Also, in the future, is there a way I can copy and paste this code instead of copying it from the screen? Is it logged somewhere? If so, can I access the log from Puppy Linux?

---

### Post by caffeinatedev on 2012-06-20
I had tried upgrading from 11.10 to 12.04 and it didn't go very smoothly (bugs from the previous release had somehow carried over). I would just try to do a fresh install of Ubuntu.

---

### Post by oldfred on 2012-06-20
Hard shutdowns can cause file corruption and in Windows a chkdsk and in Linux a e2fsck are often required to clear errors.

Best to remember the elephants when forcing a shutdown.
Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

You can try e2fsck to see if it repairs the file system.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by flyingfisch on 2012-06-20
> **oldfred said:**
> Hard shutdowns can cause file corruption and in Windows a chkdsk and in Linux a e2fsck are often required to clear errors.

Best to remember the elephants when forcing a shutdown.
Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

You can try e2fsck to see if it repairs the file system.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

OK, so if i get you right, i have to do this:

Boot in LiveCD (or Puppy, or whatever).

Run e2fsck.


I just wanted to let you know that I booted the ultimate boot cd and used HDAT2 to fix broken HDD sectors. A lot were broken repaired. 


what exactly does e2fsck do?

---

### Post by oldfred on 2012-06-20
Anytime you do not know what a command does use man.

man e2fsck

>  e2fsck - check a Linux ext2/ext3/ext4 file system
       e2fsck is used to check the ext2/ext3/ext4 family of file systems.  For
       ext3 and ext4 filesystems that use a journal, if the  system  has  been
       shut  down  uncleanly without any errors, normally, after replaying the
       committed transactions  in the  journal,  the  file  system  should  be
       marked  as clean.   Hence, for filesystems that use journalling, e2fsck
       will normally replay the journal and exit, unless its superblock  indi&#8208;
       cates that further checking is required.


Details on parameters are in the man page.

---

### Post by flyingfisch on 2012-06-20
OK, I will use man from now on :)

I am running e2fsck right now and it encountered errors so i ran the second command. Its still running. I will edit/post when it is finished.

---

### Post by flyingfisch on 2012-06-21
OK, the first command threw errors,so I did the second one, then I did the first one again. It didn't throw errors that time.


I tried booting into recovery mode again, and got the same error as last time, minus the loop complaining about broken HDD sectors.

Should I reinstall?

---

### Post by oldfred on 2012-06-21
Broken sectors do not sound good. What does Disk Utility say about the drive? It has lots of detail but all I know is if it is green it is good.

If drive is borderline do you want to keep using it?

---

### Post by flyingfisch on 2012-06-21
How do I get to disk utility?

Also, gParted seems to think its ok.

also, this HDD has had bad sectors before (2 yr ago), and it has been working good since i used HDAT2 to fix them, so if reinstalling ubuntu works and i dont have problems for a few months, i think i will keep the Hard drive

---

### Post by oldfred on 2012-06-21
If in Unity I think you just type Disk Utility.

I am using Gnome panel and it is under Applications, System Tools, Preferences. Then click on drive or partition and it has info in the right panel.

---

### Post by flyingfisch on 2012-06-21
OK, I just tried that. It says that the drive is fine. I guess ubuntu must have corrupted. 

Also,I just got the SliTaz LiveCD. Any objections to it? Would installing it be a good idea?

---

### Post by oldfred on 2012-06-21
I had Slitaz 5 running on a very old laptop as that version was the only one with the then newer kernel and drivers to use a USB to Ethernet adapter I had.  But some update broke it and I have not tried booting since.

Ubuntu actually worked on that old laptop but with only 128KB of RAM it was using so much swap as to be unusable. I had to let installer run overnight and then updates took another overnight. Slitaz worked a lot better on that old lappie. :)

---

