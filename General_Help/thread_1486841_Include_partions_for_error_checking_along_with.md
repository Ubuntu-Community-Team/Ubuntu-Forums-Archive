---
title: "Include partions for error checking along with /"
date: 2010-05-18
forum: General Help
---

### Post by linuxyogi on 2010-05-18
Hi, I have noticed that Ubuntu checks the / (which includes my home folder) for errors after a certain number of boots.

But the problem is it never checks another partition (Reiserfs) which I had created during installing Ubuntu.

I keep all my data there.

Now how do I configure Ubuntu so that it checks the partition I just mentioned ?

Please help.

---

### Post by BoneKracker on 2010-05-18
That periodic fsck on boot is determined by the "pass" setting in /etc/fstab.  I recall the reiserfs developers said dump and pass should be 0 and 0.  Based on that, I would say this periodic fsck on boot is unnecessary and not recommended for this filesystem.

I seem to recall once setting it, and that reiserfsck did run.  I'm not sure this gets you anything though, as I think maybe that filesystem takes care of checking itself automatically when it's started (and automatically running reiserfsck if there's a problem).  If you want to try it, you could set the pass value for your home directory to '2' (so it gets checked after your root directory) and see what happens.

The reiserfs development team disbanded when Hans Reiser was incarcerated and the company went under.  At least one of the developers was still maintaining reiserfs in the kernel, but I'm not sure how much of the documentation is still around.

---

### Post by linuxyogi on 2010-05-19
> **BoneKracker said:**
> 
The reiserfs development team disbanded when Hans Reiser was incarcerated and the company went under.  At least one of the developers was still maintaining reiserfs in the kernel, but I'm not sure how much of the documentation is still around.

Thanks for your reply.

Then what is your opinion ?

A) Leave the partition (Reiserfs)  as it is

                           or

B) Backup Data & format it to ext4  ?

Which filesystem do you suggest ?

---

### Post by BoneKracker on 2010-05-19
I still have a machine with reiserfs on it as its main filesystem.  In fact, it's my router/firewall, and it's the most reliable machine I have.  At the moment, if I had to bet my life on one of the two, I'd bet it on reiserfs.  I have never, ever had a problem with it (some other people will say otherwise).

So I wouldn't change it now.  What I would do is use ext4 when setting up machines in the future.  Ext4, although still fairly new, is basically stable and being actively developed/maintained.  Reiserfs is not being actively developed/maintained.  Keep in mind that ext4 itself may be replaced in the next few years by something else (e.g. btrfs).

Stick with what you've got.  Eventually you'll rebuild that machine. When you do, switch to a new filesystem.  (That's just one opinion.)

---

