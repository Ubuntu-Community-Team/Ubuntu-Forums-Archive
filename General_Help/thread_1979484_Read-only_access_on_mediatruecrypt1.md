---
title: "Read-only access on /media/truecrypt1"
date: 2012-05-13
forum: General Help
---

### Post by Welly Wu on 2012-05-13
Hi. I have an ASUS N61JV-X2 notebook PC with 8 GB of dual-channel DDR3 PC-8500 SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 GB SSD. I installed Ubuntu 12.04 64 bit Long Term Support two days ago.

I use TrueCrypt 7.1a extensively. I have a Seagate FreeAgent Desk 1.5 TB USB 2.0 hard disk drive directly connected to my ASUS N61JV-X2 notebook PC. I mounted it using TrueCrypt 7.1a normally which is to say that it was not mounted with read-only access. I checked the volume properties to confirm and it says read only access set to no. This is my primary media drive. I store my music and movies on it. I also installed Samba Server, Samba Client, and Winbind and I setup authorized Samba users to share my /media/truecrypt1 volume. My family uses an ASUS EEE PC netbook running Microsoft Windows 7 32 bit Starter Edition and a Sony VAIO laptop running Microsoft Windows 7 64 bit Home Premium. I can not write any more data to my /media/truecrypt1 volume for some unknown reason. It says that the last time that permissions were changed was back on May 6th, 2012 at 09:59:55 AM EST. I do remember changing the permissions, but I do not understand why I can not write data to my /media/truecrypt1 volume today. I used Hand Brake to rip, encode, and compress several DVD-Video movies to my /media/truecrypt1 volume yesterday.

I also have a Western Digital My Passport 2.00 TB Super Speed USB 3.0 Portable hard disk drive. I used TrueCrypt 7.1a to encrypt it using the Serpent cipher just like with my Seagate FreeAgent Desk 1.5 TB USB 2.0 hard disk drive. I never changed the permissions from the default settings on my WD portable hard disk drive. It has an exact duplicate copy of my /media/truecrypt1 volume except it is mounted as /media/truecrypt6. I can write data to the WD My Passport Portable hard disk drive.

I carefully looked at the permissions in Nautilus between /media/truecrypt1 which is my Seagate FreeAgent Desk 1.5 TB USB 2.0 hard disk drive and my Western Digital My Passport 2.0 TB Super Speed USB 3.0 Portable hard disk drive which is mounted as /media/truecrypt6 and they look identical in Nautilus.

Why can't I write data to my media/truecrypt1 volume today?

How do I fix this problem so that wellywu who is me as an Administrator can get normal access to my /media/truecrypt1 volume again?

As I wrote earlier, I just installed Ubuntu 12.04 64 bit LTS two days ago. I was using Red Hat Fedora 16 64 bit GNU/Linux earlier this week, but I decided to switch to Ubuntu recently.

What should I type in the terminal to get you more information to help?

How do I fix this problem?

---

### Post by Geffers on 2012-05-13
> **Welly Wu said:**
> Hi. I have an ASUS N61JV-X2 notebook PC with 8 GB of dual-channel DDR3 PC-8500 SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 GB SSD. I installed Ubuntu 12.04 64 bit Long Term Support two days ago.

I use TrueCrypt 7.1a extensively. I have a Seagate FreeAgent Desk 1.5 TB USB 2.0 hard disk drive directly connected to my ASUS N61JV-X2 notebook PC. I mounted it using TrueCrypt 7.1a normally which is to say that it was not mounted with read-only access.
What should I type in the terminal to get you more information to help?

How do I fix this problem?

Hi welly,

I use truecrypt too, mine is located at /usr/bin/truecrypt  As /usr/bin is normally in the filepath just typing truecrypt normally launches it.

When mine launches in obviously asks me for my truecrypt password but then my admin password.

Try launching it with sudo truecrypt from a terminal, see if that helps.

Geffers

---

### Post by Welly Wu on 2012-05-13
Now, I dismounted /media/truecrypt1 and I tried to re-mount it using the same exact password and it says that either I entered the wrong password or no truecrypt volume was found for my Seagate FreeAgent Desk 1.5 TB USB 2.0 hard disk drive. I think that I am going to reboot my computer in a few minutes to re-test TrueCrypt and the permissions.

---

### Post by Geffers on 2012-05-13
> **Welly Wu said:**
> Now, I dismounted /media/truecrypt1 and I tried to re-mount it using the same exact password and it says that either I entered the wrong password or no truecrypt volume was found for my Seagate FreeAgent Desk 1.5 TB USB 2.0 hard disk drive. I think that I am going to reboot my computer in a few minutes to re-test TrueCrypt and the permissions.

Reboot often solves all ;)

Geffers

---

### Post by Welly Wu on 2012-05-13
The problem resolved itself after I rebooted my ASUS N61JV-X2 notebook PC running Ubuntu 12.04 64 bit Long Term Support! I can now use my /media/truecrypt1 volume or my Seagate FreeAgent Desk 1.5 TB USB 2.0 hard disk drive normally again. In fact, I am using Hand Brake snapshot version to rip, encode, and compress a DVD-Video movie that I purchased and it is being saved onto my /media/truecrypt1 volume right now. I guess that the previous read-only access error was an aberration. I am marking this thread as solved now.

---

### Post by Geffers on 2012-05-13
> **Welly Wu said:**
> The problem resolved itself after I rebooted my ASUS N61JV-X2 notebook 

 I am marking this thread as solved now.

Glad all is well.

Geffers

---

