---
title: "please help download problem"
date: 2010-05-20
forum: General Help
---

### Post by vvfrn on 2010-05-20
I tried installing ubutuntu with Xp , but then the hardrive got corrupted. So I got the ubuntu Cd and tried to wipe it and only install Ubuntu , but something happened. Now when I start the computer it says no boot device. Therefore, I got the 10.04 Cd and installed it in the process it said that there is an unrecoverabl error and to boot into the desktop session in order to trobleshoot it. please help in troublshooting it.

---

### Post by vvfrn on 2010-05-20
I tried installing ubutuntu with Xp , but then the hardrive got  corrupted. So I got the ubuntu Cd and tried to wipe it and only install  Ubuntu , but something happened. Now when I start the computer it says  no boot device. Therefore, I got the 10.04 Cd and installed it in the  process it said that there is an unrecoverabl error and to boot into the  desktop session in order to trobleshoot it. please help in  troublshooting it.

---

### Post by Zyrtec on 2010-05-20
Have you double checked the hard drive connection to the motherboard? Does your BIOS list the hard drive as actually being in your computer (is it listed as a bootable device when changing the boot order)?

It could possibly be a failing hard drive.

---

### Post by vvfrn on 2010-05-20
I dont know how to check the hardrive connection to the motherboard, but I know that when  into the bios there are a bunch of options in boot priority. Also, I am in the desktop session right now and when I did a disk test it detected the Fijitsu hardrive.  Thanks for responding. I appreciate it.

---

### Post by tottenham12712 on 2010-05-20
go to basically any manufacturer of hdds and go to support and download there disk utility. 

For instance i use Fujitsu HD utility disk, in short it is a small cli software that can scan your drive for errors and possible fix them...if not try a reformat make sure you do a full with either all 1's or all 0's

I have the software that i can send you through an ftp link if you cant find it so let me know PM me

Dylan

---

### Post by lisati on 2010-05-20
> **vvfrn said:**
> [COLOR="Red"]I dont know how to check the hardrive connection to the motherboard,[/COLOR] but I know that when  into the bios there are a bunch of options in boot priority. Also, I am in the desktop session right now and when I did a disk test it detected the Fijitsu hardrive.  Thanks for responding. I appreciate it.

How comfortable are you opening the cover of your computer and checking the plugs and cables? (Recommend turning off your computer before trying this, and take precautions to avoid zapping yourself or your computer accidentally)

---

### Post by MooPi on 2010-05-20
If you can boot to the Live CD you can start a program called gparted. It sounds as if you can do this , correct me if I'm wrong. Gparted is a comprehensive format and partitioning tool. While in the live session and using gparted delete all existing partions and re-install Ubuntu. As mentioned in the previous post, your hard drive may be failing also best of luck.

---

### Post by vvfrn on 2010-05-20
> **tottenham12712 said:**
> go to basically any manufacturer of hdds and go to support and download there disk utility. 

For instance i use Fujitsu HD utility disk, in short it is a small cli software that can scan your drive for errors and possible fix them...if not try a reformat make sure you do a full with either all 1's or all 0's

I have the software that i can send you through an ftp link if you cant find it so let me know PM me

Dylan
That would be great!! Thanks I would appreciate it if you send me the link.

---

### Post by vvfrn on 2010-05-20
> **MooPi said:**
> If you can boot to the Live CD you can start a program called gparted. It sounds as if you can do this , correct me if I'm wrong. Gparted is a comprehensive format and partitioning tool. While in the live session and using gparted delete all existing partions and re-install Ubuntu. As mentioned in the previous post, your hard drive may be failing also best of luck.


I am familiar with that program. however, there are no partitions(only one 37gb partition that says unallocated).

---

### Post by ubunterooster on 2010-05-20
> **vvfrn said:**
> I am familiar with that program. however, there are no partitions(only one 37gb partition that says unallocated).
You need to allocate it by turning it into, say, a ext4 partition

---

### Post by vvfrn on 2010-05-20
Thanks you everyone I changed it to ext 4 format and now it finally works!!! XD

---

### Post by cariboo on 2010-05-20
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by tottenham12712 on 2010-05-20
his problem isnt related to partitions due to the fact that linux can read any type of file format. altho the os needs a ext5. his problem is more than likely to many bad sectors and the arent being relocated

---

