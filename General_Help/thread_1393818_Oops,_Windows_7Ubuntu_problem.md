---
title: "Oops, Windows 7/Ubuntu problem"
date: 2010-01-29
forum: General Help
---

### Post by RMcD94 on 2010-01-29
I did a search for Windows 7 topics, but none fit what I have done.

Basically put I installed Ubuntu 9.10 (I think it was the desktop version, though I meant to get the laptop one, since it is a laptop after all) completely over Windows 7. After a few days of Ubuntu I was missing Windows 7 too much so I searched around for the disk and stuck it in. 

Using the advanced format option thing, I formatted away everything, and started the Windows 7 install on my entire disk (spending annoying minutes to get that 100 MB System thing away from occupying C:/). 

Some half an hour in an error popped up. I didn't think to write the error down, but I do know it was because a .dll file was missing. I understand that apparently installing Windows over Ubuntu is difficult, and probably should have given this more attention.

The error occurs somewhere at ~38% (I think), while extracting the Windows files. It is Windows 7 Ultimate. I have a screenshot of my system information uploaded somewhere on the internet. Ah ha, found it:

[http://img49.yfrog.com/img49/7774/sn3r.jpg](http://img49.yfrog.com/img49/7774/sn3r.jpg)

I don't know if that helps, but there you go in any case.

Now, for my question. How can I install Windows 7, 32 bit, onto my computer without having to install Ubuntu again? If I have to install Ubuntu again, I think that there is probably a guide already for how to install Windows 7 completely over Ubuntu, without having already removed Ubuntu. A link to that would be nice though. Also most of the guides referred to the beta version of Windows 7.

Urm, I decided to go with [ubuntu] tag, maybe I should have gone with the other_os one.

---

### Post by Vaphell on 2010-01-29
you don't need to install anything in order to install win7. If win7 installer doesn't recognize linux partitions on the hard drive and can't utilize whole disk space all you may need to do is to boot from ubuntu live cd (without installing) and use gparted to kill those with ext2/3/4 filesystems.

That .dll error is strange though but it's not ubuntu's fault.

---

### Post by RMcD94 on 2010-01-29
Thank you, I will try that right now.

---

### Post by howefield on 2010-01-30
> **RMcD94 said:**
> Basically put I installed Ubuntu 9.10 (I think it was the desktop version, though I meant to get the laptop one,

There is no seperate version for laptops. You got the right one.

> Some half an hour in an error popped up. I didn't think to write the error down, but I do know it was because a .dll file was missing.

Where did you get the Windows 7 disk from ? It sounds like a defect on the disk.

---

### Post by RMcD94 on 2010-01-30
> There is no seperate version for laptops. You got the right one.

Hrm, I thought there was, I saw it mentioned.

> Where did you get the Windows 7 disk from ? It sounds like a defect on the disk.

I used the disk before, when I upgraded from Vista. I might have been scratched or something in the, hmm, 4 months since.

>  all you may need to do is to boot from ubuntu live cd (without installing) and use gparted to kill those with ext2/3/4 filesystems. 

I booted from the disc, and choose the without installing button. I then downloaded GParted, which was an .iso file. So, if I understand right, I'll need to burn the .iso to a disc, and then use that to do something to the (single) partition.

---

### Post by RMcD94 on 2010-02-04
Urm, it's still broken.

---

### Post by x C0MMAND0 x on 2010-02-04
There is no "laptop" version of Ubuntu, though there is a "Netbook" version that is tailored to be lighter and more efficient for netbooks.  For laptops I use the regular "desktop" version.

---

### Post by RMcD94 on 2010-02-14
Okay. I managed to remove GRUB. So now my computer has nothing on it whatsoever. If I start it without a disc, it comes up BOOTMGR is missing. 

So I tried installing Windows 7 again. 

I choose format, custom, a made a new partition from the whole drive. With partition 1 being turned into 100 MB worth of System Reserved. I begin the installation on the remaining memory on Partition 2.

It is happily to copy files, but once it begins extracting them this error appears (after a few minutes):

"Windows cannot install required files. The files may be corrupt or missing. Make sure all files required for the installation are available and restart the installation. Error code: 0x80070017"

I burned the .iso to at least three separate discs and this error occurred on each. Now, I have no idea how to fix it.

Edit: I guess this has nothing to do with Ubuntu now, so I googled to find this.

[http://windows7forums.com/windows-7-installation-upgrade/7116-error-0x80070017-expanding-files-0-cannot-install-required-files.html](http://windows7forums.com/windows-7-installation-upgrade/7116-error-0x80070017-expanding-files-0-cannot-install-required-files.html)

---

### Post by Kai69 on 2010-02-14
I used the disk before, when I upgraded from Vista. I might have been scratched or something in the, hmm, 4 months since.

Is the W7 disk an upgrade disk or install disk? If its an install disk when installing I would delete all partitions and let W7 do its stuff it will sort things like mbr and swap out itself .

---

### Post by RMcD94 on 2010-02-14
Urm, I can upgrade and install. But every time I've used it, I used the custom install option, because I didn't care about anything.

---

