---
title: "Ubuntu won't recognize my Seagate external hard drive"
date: 2011-02-09
forum: General Help
---

### Post by Acedrew89 on 2011-02-09
The title basically says it. I can't get Ubuntu to recognize my external hard drive. The weird part is it must be reading it on some level since everything Ubuntu is on the external hard drive.

Any way, I only want to install the Ubuntu OS on the external hard drive so it's fairly imperative that I be able to see it.

The hard drive is a Seagate 320gig external hard drive, the small USB (1.1?), and is formatted to FAT32.

Any help or thoughts?

---

### Post by quadproc on 2011-02-09
> **Acedrew89 said:**
> The title basically says it. I can't get Ubuntu to recognize my external hard drive. The weird part is it must be reading it on some level since everything Ubuntu is on the external hard drive.
What does gparted say in its little window in the upper right corner as you scroll through the possibilities?  Are you running from a Live CD?  From a USB stick?Something  else?
> 
The hard drive is a Seagate 320gig external hard drive, the small USB (1.1?), and is formatted to FAT32.
That drive should work OK. Are you using USB instead of SATA?  If not, did you install or remove the little jumper for speed control?  I hope that you don't mean USB 1 as opposed to USB 2 - that would be awfully slow.  You may wish to change the format away from FAT - that old format will impose some unwelcome limitations on what you can store on the disk.  I would suggest ext3 or ext4.  Or, if you must share data with a Microsoft OS, then you may be able to tolerate NTFS but it lacks a lot.

quadproc

---

### Post by Acedrew89 on 2011-02-10
Okay I have figured some things out and now I have Ubuntu fully installed and on the Seagate hard drive (micro USB is what I meant), I still can't physically see the external hard drive though while in Ubuntu, but when I go into the disk analyzer it says I have all of the 300 gigs plus the 150gig internally. I have to mount the internal drive, so my guess is that the external drive is the primary mounted drive and it doesn't necessarily show anywhere (like in Computer), but it is there in the sense that I allocated 200+gigs for the /home. Thoughts?

---

### Post by Mark Phelps on 2011-02-11
Sorry ... but your post is confusing to  me ...

You said "everything Ubuntu" is on that drive -- implying that you are booting and running Ubuntu from the external hard drive. Right?

But then, you say you want to format the drive and install Ubuntu on it!!

You can't format the same drive you're using to run Ubuntu.  So, if that is your question, it can't be done.  You will have to boot using something else (i.e., Ubuntu LiveCD, Ubuntu installed on an internal drive) in order to format the external drive.

---

### Post by Acedrew89 on 2011-02-12
Sorry to have confused you. Everything is all set now. I appreciate all of your help.

Thanks,
Andrew

---

