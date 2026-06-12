---
title: "Corrupted OS"
date: 2011-10-23
forum: General Help
---

### Post by edmund085 on 2011-10-23
I have Ubuntu installed on the Hard Drive. The Power Supply Unit got busted so I transferred the Hard Drive into another CPU. It didn't work at first so I decided to fix the busted PSU and returned it to the original CPU. As I returned it, all I get is a black screen, I waited for 1 hour and still not a thing. My question is that If I install the Ubuntu OS again, will it delete my files or will it remain? (I want a valid and a strong answer, since I heard rumors that installing the Ubuntu OS will not affect your files in the Hard Drive).

---

### Post by tartalo on 2011-10-23
If it doesn't boot the first thing I'd test is if the Hard drive is working and if the partition and file system(s) are OK. Boot form a Live and try to access your partitions. Is everything there?

---

### Post by edmund085 on 2011-10-26
the hard drive is working... I used the LIVECD but I don't know how to use it...

---

### Post by jamesisin on 2011-10-26
If you do a clean installation of Ubuntu onto that same hard drive (and partitions) you will overwrite any data there contained.

Was the drive able to boot in the other machine?

Can you use that drive in a USB tray to boot from this original machine?

---

### Post by rng on 2011-10-26
> **edmund085 said:**
> the hard drive is working... I used the LIVECD but I don't know how to use it...

The livecd should boot into regular desktop. From there see if you can access the hard drive and its folders. Copy any needed files to a usb pendrive.

---

### Post by Mark Phelps on 2011-10-26
When you BOOT from a LiveCd, eventually, you will get to a screen that has two choices: Try Ubuntu or Install.  Choose the Try option.  Eventually, that will get you to a desktop.

From there you can use Ubuntu in the same manner as you usually do, it will just be slower as it has to load stuff from the CD instead of the hard drive.

---

### Post by edmund085 on 2011-10-29
i tried using the LiveCD, i accessed the format but it wont let me, it gives an error saying that i cannot access it it is not mounted.

---

### Post by rng on 2011-10-29
It will help if you give more details. Which livecd did you use (ubuntu or some other). How did you try to access the hard drive- from command line or from top menu item 'Places'. 

Output of following commands will also be helpful: 

$ sudo fdisk -l        

$ sudo mount 


(NOTE: -l is small L and not 1(one))

---

### Post by 3rdalbum on 2011-10-29
Use the manual partitioning method in the Ubuntu installer. In the latest version of Ubuntu, in the installer it has a list of options (Erase hard disk, resize partition etc) and then at the bottom it has the option "Something Else?".

Choose that. It brings you to a screen where you can do some basic partitioning. Click on your old Ubuntu partition and click Edit...

Change the "Mount Point" to /

Click OK.

Make sure that the "Format?" checkbox is NOT ticked for the existing Ubuntu partition.

The Ubuntu installer will now install Ubuntu again, and preserve the contents of the /home directory on the old Ubuntu. 100%, for sure. Just as long as the "Format?" checkbox is not ticked.

---

### Post by edmund085 on 2011-10-30
first thing first.... I'm not used to ubuntu and I dont understand a thing about what you said rng. 

3rdalbum ok.. i understand completely well, I have used a passphrase on my Ubuntu or a password. So it means its encrypted. Does this means my passphrase will still be desame aor my password will still remain?

---

### Post by edmund085 on 2011-10-30
I have even more bad news, I just misplaced or lost my passsphrase. I don't know where I placed it. May I ask, can I just make my own password without using passphrase?

---

### Post by jamesisin on 2011-10-30
That could make things, um, complicated.  I believe that if you log in you don't need your passphrase; also, if you login with your password you can change your passphrase.  Outside of that you really need that passphrase to get past the encryption.

---

