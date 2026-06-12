---
title: "I screwed up, badly."
date: 2011-06-26
forum: General Help
---

### Post by Hovercat on 2011-06-26
Hello. Last night I was installing Ubuntu 11.04, and after using it, it stopped working right and the visual styles stopped working. I hated Unity as well, so I wanted to install 10.10. I downloaded 10.10, and when I got to the partitioning menu, I chose advanced and deleted the 2 linux partitions and since it's 2AM and I'm extremely tired and not paying attention, I made one linux partition and set my Windows partition to swap space. I need to recover what is on my Windows partition, then I can format the entire hard drive and start now.

My question is, how do I retrieve my files from the linux swap space?

I cannot boot into Windows, nor can I boot into Ubuntu because for some reason, Grub is screwed up.

---

### Post by WorMzy on 2011-06-26
Try using [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") from a live CD. Make sure to run

```
swapoff
```

immediately after booting, so that any risk of writing to the swap partition is eliminated.

---

### Post by Hovercat on 2011-06-26
> **WorMzy said:**
> Try using [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") from a live CD. Make sure to run

```
swapoff
```immediately after booting, so that any risk of writing to the swap partition is eliminated.


I can't find the live CD.

---

### Post by Hovercat on 2011-06-26
I know I'm not supposed to bump, but I REALLY need the files with my MySQL and other passwords. They're 2 .txt files and that is all I need.

---

### Post by apollothethird on 2011-06-26
> **Hovercat said:**
> I can't find the live CD.

You'll have to download the live CD and create another one.  The perform the steps given to you by Hovercat.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Hovercat on 2011-06-26
> **apollothethird said:**
> You'll have to download the live CD and create another one.  The perform the steps given to you by Hovercat.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Is BootMed fine?

---

### Post by dirty_harry on 2011-06-26
[http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)
[http://www.knoppix.org/](http://www.knoppix.org/)

there are vista/w7 recovery cds out there, with fixboot/fixmbr... but my experience is that testdisk works better.

if you really fear data loss you should make an image before trying any tools!
which reminds me to backup my own stuff now.

---

### Post by Hovercat on 2011-06-26
> **dirty_harry said:**
> [http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)
[http://www.knoppix.org/](http://www.knoppix.org/)

there are vista/w7 recovery cds out there, with fixboot/fixmbr... but my experience is that testdisk works better.

if you really fear data loss you should make an image before trying any tools!
which reminds me to backup my own stuff now.

I don't think the Windows 7 recovery tool will work because my Windows partition is linux-swap. Am I wrong?

---

### Post by sanderj on 2011-06-26
Boot from a live-Ubuntu-CD (or USB-stick), and see which partitions are available and if there's still a Windows partition. If not, and it has been reformatted to swap, I don't know if/how you can get files back.

---

### Post by Hovercat on 2011-06-26
Ugh for ***** sake! I don't know what I'm going to do now...

How can I reset a user password and the root password on Ubuntu server edition?

There is one user I have the password for but that user is not in the sudoers file. If I can reset the passwords I don't need to worry about getting these backed up, because I can change my PayPal password and I might be able to change my MySQL passwords.

---

### Post by nerdy_kid on 2011-06-26
You probably can get the files back.  First, you need your Ubuntu CD.  Boot the system off of the CD.  Before you login, press <ctrl> <alt> <F1>, login, and type:  
```

sudo swapoff -a

```
press <ctrl> <alt> <F7> and login normally.
Open firefox and go to [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download) and download the appropriate file.  Extract the download, open a terminal, type:

```

sudo -i

```

cd into the extracted file you downloaded and run
```

./testdisk_static

```

follow the prompts, and before long you should have your ex-windows partition being scanned for files.  

Note, that if you didn't actually _use_ the swap partition then it should be really easy (i.e. ignore most of the above) -- I'll get back to you with additional info.

---

### Post by Hovercat on 2011-06-26
> **nerdy_kid said:**
> You probably can get the files back.  First, you need your Ubuntu CD.  Boot the system off of the CD.  Before you login, press <ctrl> <alt> <F1>, login, and type:  
```

sudo swapoff -a

```press <ctrl> <alt> <F7> and login normally.
Open firefox and go to [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download) and download the appropriate file.  Extract the download, open a terminal, type:

```

sudo -i

```cd into the extracted file you downloaded and run
```

./testdisk_static

```follow the prompts, and before long you should have your ex-windows partition being scanned for files.  

Note, that if you didn't actually _use_ the swap partition then it should be really easy (i.e. ignore most of the above) -- I'll get back to you with additional info.


It's asking for partition table type. should I choose Intel/PC?

---

### Post by apollothethird on 2011-06-26
> **Hovercat said:**
> I know I'm not supposed to bump, but I REALLY need the files with my MySQL and other passwords. They're 2 .txt files and that is all I need.

If you have physical access to the mysql machine you can easily reset your root password.    Recovering your passwords from Paypal, your banks, and other servers should also be simple as long as you have access to your email account for verification.  Just follow their steps for lost passwords.

For mysql you can:

```
1. Stop mysqld and restart it with the --skip-grant-tables --user=root options (Windows users omit the --user=root portion).
2. Connect to the mysqld server with this command:
   shell> mysql -u root
3. Issue the following statements in the mysql client:
   mysql> UPDATE mysql.user SET Password=PASSWORD('newpwd')
       ->                   WHERE User='root';
   mysql> FLUSH PRIVILEGES;
   Replace "newpwd" with the actual root password that you want to use.
4. You should be able to connect using the new password.
```-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Hovercat on 2011-06-26
> **apollothethird said:**
> If you have physical access to the mysql machine you can easily reset your root password.    Recovering your passwords from Paypal, your banks, and other servers should also be simple as long as you have access to your email account for verification.  Just follow their steps for lost passwords.

For mysql you can:

```
1. Stop mysqld and restart it with the --skip-grant-tables --user=root options (Windows users omit the --user=root portion).
2. Connect to the mysqld server with this command:
   shell> mysql -u root
3. Issue the following statements in the mysql client:
   mysql> UPDATE mysql.user SET Password=PASSWORD('newpwd')
       ->                   WHERE User='root';
   mysql> FLUSH PRIVILEGES;
   Replace "newpwd" with the actual root password that you want to use.
4. You should be able to connect using the new password.
```-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

I had my host reset my password.

I also had all of my passwords reset, so I don't care about file recovery anymore. But now during the Windows installation, it says "Setup was unable to create a new system partition or locate an existing system partition. See the Setup log files for more information."

---

### Post by -kg- on 2011-06-26
> **Hovercat said:**
> I had my host reset my password.

I also had all of my passwords reset, so I don't care about file recovery anymore. But now during the Windows installation, it says "Setup was unable to create a new system partition or locate an existing system partition. See the Setup log files for more information."

Probably because you reformatted the original Windows partition to swap.  You'll likely need to delete (or shrink it to the right size if you want to retain it) the swap file in order to give Windows some free space to install in.  Shrink it from the left in order to give Windows space at the beginning of the drive in which to create its partition and install in.

Then you'll need to restore the GRUB bootloader (or whatever bootloader you use) into the MBR in order to use Linux again.  Windows is funny that way (but why am I not laughing?).

If you need it, read at the link in my signature block for further information on partitioning operations.

---

### Post by Quackers on 2011-06-26
Here is a guide for using testdisk
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

Although, if you are installing something it seems you have moved the goalposts somewhat.

---

### Post by Hovercat on 2011-06-26
> **-kg- said:**
> Probably because you reformatted the original Windows partition to swap.  You'll likely need to delete (or shrink it to the right size if you want to retain it) the swap file in order to give Windows some free space to install in.  Shrink it from the left in order to give Windows space at the beginning of the drive in which to create its partition and install in.

Then you'll need to restore the GRUB bootloader (or whatever bootloader you use) into the MBR in order to use Linux again.  Windows is funny that way (but why am I not laughing?).

If you need it, read at the link in my signature block for further information on partitioning operations.

I've formatted it from Windows using a SATA-to-USB adapter, I still got the error. I tried formatting and removing the partition in Ubuntu from the live CD, and I still got the error. I may as well buy a new hard drive at this point.

---

### Post by nerdy_kid on 2011-06-26
> **Hovercat said:**
> It's asking for partition table type. should I choose Intel/PC?

yeah, unless it is a mac.  I think testdisk does it's best to autodetect the partition table type anyway, so the default should be safe.

---

### Post by Hovercat on 2011-06-26
> **nerdy_kid said:**
> yeah, unless it is a mac.  I think testdisk does it's best to autodetect the partition table type anyway, so the default should be safe.

It didn't work, but now I have an error while installing Windows 7.

---

### Post by nerdy_kid on 2011-06-27
> **Hovercat said:**
> It didn't work, but now I have an error while installing Windows 7.

You need to format the disk -- forgot how to get to that option in the Win7 setup though

---

### Post by Hovercat on 2011-06-27
> **nerdy_kid said:**
> You need to format the disk -- forgot how to get to that option in the Win7 setup though

I figured it out. I re-partitioned the drive in FDISK, but this time I changed the partition ID to 87. (NTFS)

---

