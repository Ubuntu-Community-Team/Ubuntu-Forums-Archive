---
title: "Accidentally recovered system... wtf?"
date: 2009-10-16
forum: General Help
---

### Post by Gizenshya on 2009-10-16
(my question is at the end.  the rest is an explanation)

I've tried a few times to no avail in the past to recover an ubuntu installs after windows crashes, which typiucally take wubi's with them.  Every time I've had to reinstall fresh and reinstall everything, instead of just going from copying the wubi disk as planned.

Well, I finally got everything in Ubuntu just how I wanted it and before I could try copying it, windows crashed and took my poor wubi install with it.  I haven't tried to recover it yet, though I had planned on starting to try in the next few days.  This is on hard drive "A"

Well...  Today I installed ubuntu through wubi on another hard drive (hard drive "B").  Well, hard drive A is slaved in the system, and I didn't do anything with it at all during wubi installation.

Everything until now is fine.  BUT, when I booted into the "fresh" ubuntu install on hard drive B... it was exactly the crashed wubi ubuntu install that was installed on hard drive A.  How the *bleep* did I manage to that? :confused::confused::confused:

I'm not complaining... this is like a dream come true.  I very much wanted all the programs and files off of the previous subi installation... it just wasn't expected.  I'm very pleased that it worked out like it did.

My question:  How did this happen?  I have no idea where to begin to start trying to figure out what happened.  As much as I like that it happened, it was unexpected.  I would like to know how and why it happened, so I can do it again (or avoid it, for that matter) in the future.

thanks in advance

---

### Post by Shibblet on 2009-10-16
> **Gizenshya said:**
> My question:  How did this happen?  I have no idea where to begin to start trying to figure out what happened.  As much as I like that it happened, it was unexpected.  I would like to know how and why it happened, so I can do it again (or avoid it, for that matter) in the future.

thanks in advance

If you have a Wubi installation, and Windows crashes, sounds like Windows took it's boot-loader with it.  So there is no way to boot into Windows (Crashed) or Ubuntu, because the boot-loader is gone.

I'm not 100% sure how it happened, but I do know how you can avoid it in the future.  Do not use Wubi.  Install Windows, then install Ubuntu.  Grub will be installed and allow you to choose between your OS's at boot, the same way Wubi uses the Windows boot-loader.

Now, if either of your OS's crash, and need re-installation, you can still boot to the other OS.

---

### Post by Gizenshya on 2009-10-16
yeah windows took the bootloader with it, and yeah I know I can just use a full install and not worry in the future.  But I don't want to do that for a couple reasons, that are out of the context of this thread (don't want to spend too much time on that).

the thing that is so strange for me is that the install it copied was on a slave drive.  the drive that I installed it to has never had an installation of linux before.  I don't know why it looked there.

is there maybe something I checked or did that made it do that, without me even realizing it?

Another thing... the drive that it copied the ubuntu installation from doesn't show up for mounting when I go to look at the drives window.  I don't know if that is important... but the drive is physically hooked up to the computer.

---

### Post by Gizenshya on 2009-10-16
more info

Apparently it didn't copy the old wubi installation... it is booting from it.

If I have the slave drive (drive A, with the original wubi installation) installed, when I select Ununtu from the windows boot menu it loads from the wubi from the slave drive A.

But, if I select ubuntu the same way, but without the slave drive hooked up, it boots from the fresh wubi of the master drive.

how can this happen?

---

### Post by wilee-nilee on 2009-10-17
You might want to consider dual-booting rather then wubi installs there are inherent problems with having Ubuntu run inside of windows some of them you have mentioned.

---

### Post by oldfred on 2009-10-17
I do not know wubi, but all installs normally rewrite the MBR on the first disk as that is what the system boots. Grub is normally smart enough to find most operating systems and add entries. I expect for wubi it found the old entry and updated it and by updating it corrected the problem. Do you have two wubi entries & a windows entry in your boot?

If XP you probably can look at boot.ini to see the entries for booting. Do not change anything or else it may not boot again.

---

