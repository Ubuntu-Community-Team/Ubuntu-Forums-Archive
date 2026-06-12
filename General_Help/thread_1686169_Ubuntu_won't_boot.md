---
title: "Ubuntu won't boot"
date: 2011-02-11
forum: General Help
---

### Post by 80sDweeb on 2011-02-11
I’ve got a fairly recent (4 or 5 months old?) Ubuntu install that suddenly refuses to boot.  It takes me into:

error: couldn't read file.
error: you need to load the kernel first.

  Failed to boot both default and fallback entries.

Press any key to continue...

Pressing a key takes me into GRUB.

From GRUB, I select the first line, which is:

Ubuntu, with Linux 2.6.35-23-generic

I’m taken to an entirely blank page that sits there for most of a minute, then the page goes black for an instant, then quickly scrolls through lots of text and ends at some lines that say:

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter ‘help’ for a list of built-in commands.

(initramfs)

A few lines above this it has some lines where it's saying how mount bla failed, couldn't find device, or something like that.

It feels like I’ve lost a big part of my filesystem.  Is there something I can do with a livecd to diagnose this?  I have a data drive that started out as NTFS, that I did some sort of change to so that Ubuntu could use it with my data intact (I can’t remember what exactly) and I’d REALLY like to see that data again...

Thanks for any tips.

Scott in Penfield

---

### Post by Arand on 2011-02-11
Presumably you edited the /etc/fstab file, yes?

If you just boot a liveCD you should be able to access the data you have on the NTFS partion simply by using the file browser.

Also, you should be able to access the filesystem of the non-working install, and if you know what you edited wrong in fstab for example you should be able to fix it.

It may be good to post your fstab file here for the installed system if the solution isn't trivial.

EDIT: Hmm, that might also be grub not seeing the correct partiition as well... the bootinfo script might give some information that could clue that: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
:ENDEDIT
- arand

---

### Post by 80sDweeb on 2011-02-11
I didn't edit anything, I actually don't even look at this system, I use it as a file server, accessing the data on the old Windows drive from Windows XP machines around the house.  I've always suspected something flaky about this box, it would "freeze up" every few weeks or so, requiring a hard reboot.  This time, it froze up yesterday, I tried to reboot and got nothing.

If I get a look at the system with a LiveCD, what can I do to restore the system?  I'd LOVE it if the Samba configuration I did months ago didn't have to be completely redone.

Scott in Penfield NY

---

### Post by williamts99 on 2011-02-12
> **80sDweeb said:**
> I've always suspected something flaky about this box, it would "freeze up" every few weeks or so, requiring a hard reboot.  This time, it froze up yesterday, I tried to reboot and got nothing.

If I get a look at the system with a LiveCD, what can I do to restore the system?  I'd LOVE it if the Samba configuration I did months ago didn't have to be completely redone.

Scott in Penfield NY

With the liveCD you can copy your configuration files and back up what you need to.  I would also test the ram with the liveCD and do some hard drive tests.

It might be as simple file system error, or could be a hardware failure, I would use a LiveCD to dig in and find out where you stand.

---

### Post by 80sDweeb on 2011-02-12
Going in with the LiveCD I got a warning that one of my drives was failing, and that many sectors were bad.  I guess a critical file (or many files) is sitting on one of those bad sectors.  I'll have to find another drive and see if this system is stable after all.  In the meantime, I put the data drive into a USB external enclosure and attached it to a WinXP system on the network, and all the files showed up just fine.  Whew!

Scott in Penfield NY

---

### Post by williamts99 on 2011-02-12
> **80sDweeb said:**
> Going in with the LiveCD I got a warning that one of my drives was failing, and that many sectors were bad.  I guess a critical file (or many files) is sitting on one of those bad sectors.  I'll have to find another drive and see if this system is stable after all.  In the meantime, I put the data drive into a USB external enclosure and attached it to a WinXP system on the network, and all the files showed up just fine.  Whew!

Scott in Penfield NY

That is never a good sign, usually that is based on SMART reporting, but I would do a complete set of diagnostics on the drive.  There are many resources for a live CD to do that with(after backing up the important files), like Hirens, Ultimate, or FalconFour boot CDs.

All hard drives eventually fail, the only question is when.

Good Luck

---

