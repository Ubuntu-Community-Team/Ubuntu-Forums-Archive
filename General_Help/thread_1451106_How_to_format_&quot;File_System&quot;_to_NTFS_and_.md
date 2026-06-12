---
title: "How to format &quot;File System&quot; to NTFS and install Win 7?"
date: 2010-04-10
forum: General Help
---

### Post by MKVCrazy on 2010-04-10
I tried to install Win 7 from the DVD and it didn't work at first because my Ubuntu is not in NTFS which is require for Win 7 to start installing. But the Win 7 doesn't have the option to format the harddrive for me so I went back to Ubuntu to format it.

I downloaded GParted and NTFSProgs

The storage drive in the screenshot below the one I want to format but if I format that while I am running the Ubuntu OS, what will happen? Can someone guide me what to do? I can see there are two seperate virtual drives in that one 320GB SATAII harddrive. I want to erase the one with the more space because I'll install the Win 7 on it since it requires 15GB+ space. I do not want to have a dual boot by the way so I also want to make sure no Ubuntu is left out.

Regards,
MKVCrazy

---

### Post by cogier on 2010-04-10
If you can I suggest you format the whole disk to NTFS using GParted running from a Ubuntu live CD, that way the drive you want to format will not be mounted. Then install Windows 7 then install Ubuntu.

Windows will not look for another operating system but Ubuntu will.

---

### Post by aklo on 2010-04-10
i'm not sure how to do it but incase you don't know yet...

Having linux installed first and afterwards installing windows will destroy your dual boot stuff...and you may have to go through a complicated process to get back dual booting ...or you may not even get it back...

That is why i always install windows first then ubuntu.

---

### Post by Mark Phelps on 2010-04-10
Actually, all you have to to is shrink the Ubuntu partition to the right and leave an unallocated space on the left for Win7.  It can then format that space as part of the installation.

But since the Ubuntu partition is mounted when you're using it, you'll need to either boot from the Ubuntu LiveCD and ensure that the Ubuntu partition is unmounted, or download and burn a GParted LiveCD from distrowatch.com and use that.

You WILL have to reinstall GRUB2 after you install Win7 -- there's no way around that.  But there are plenty of threads on how to do that.

---

### Post by Wardje on 2010-04-10
He says he doesn't want to dual boot guys :P

As has been said, use a Ubuntu Live CD. This way you can format the harddrive properly since it (should not) be mounted.

---

### Post by Klone1222 on 2010-04-18
What if you can't access the internet to get the download(s)? How can you format File System?

---

