---
title: "GRUB Issues (Error 22)"
date: 2011-04-03
forum: General Help
---

### Post by burkhardt on 2011-04-03
Hello all,

About two years ago I installed Ubuntu and GRUB on my four year old Lenovo T61 laptop as a dual boot with Windows XP. Yesterday I realized how little room I had on my Windows Partitions (a grand total of 4G) and I needed about 7G, so I decided to remove Ubuntu since I hadn't used it in ages and had forgotten my username/password, so I fired up my GParted boot disk and wiped my Ubuntu partitions and resized my Windows partitions to fill the unused space. When I started my laptop GRUB gave me an Error 22 message. I have been reading about how to solve this problem on many forums and tried their fixes, but nothing has worked yet. I am currently working off of an Ubuntu Live CD. I have access to a CD/DVD burner. I do not want to reinstal a Linux distro since I desperately need the space. I wish to either completely remove GRUB and use the standard Boot system from Windows, or fix it, I have no real preference, but please any and all help is greatly appreciated!

-Burkhardt

---

### Post by Rubi1200 on 2011-04-04
Although you removed Ubuntu, vestiges of the GRUB bootloader were left over in the MBR.

If Windows is now the only operating system on the computer, the simple fix is to restore its bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by burkhardt on 2011-04-04
Okay Thank You!

I looked at the post for fixing the windows xp boot loader. I do not have a Windows xp installation cd, since this computer was standardized by my school, so they essentially sent it to me finished and with only an instruction manual. Do you know any site that has a free download for an iso of it? (I have been looking for a bit, but can't seem to find anything :/ )

-Burkhardt

---

### Post by Rubi1200 on 2011-04-04
I don't know of a site for an XP disk. I know they are available for Vista and 7, but since the boot partitions are built differently on those versions it wouldn't help you in this situation.

However, what you can do is install a Windows-like bootloader from the Ubuntu LiveCD:

start the CD and choose the option to try Ubuntu.

Go to System > Administration > Synaptic Package Manager > Settings > Repositories and make sure universe is enabled.

Then run these commands in the terminal:

```
sudo apt-get update
sudo apt-get install lilo 
sudo lilo -M /dev/sda mbr
```
This assumes you only have one drive and it is designated as sda. If not, change to reflect the correct drive e.g. sdb, sdc etc.

Ignore any warnings during the installation of lilo and let it continue to install to the MBR of the drive.

When it is finished, reboot taking out the CD and you should be back in Windows again.

If you want to wait for other opinions about an XP CD that is your prerogative.

---

### Post by burkhardt on 2011-04-04
Okay I just tried that, and this is what it spit out:

ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg [189B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [198B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg [198B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release [74.6kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [57.9kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release [57.9kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages [1253kB]                  
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [242kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2590B] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [131kB]         
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [693B]    
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages [8848B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources [555kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources [3156B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages [322kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages [3789B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources [158kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources [1330B]
Fetched 2870kB in 4s (605kB/s)  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$ sudo apt-get install lilo
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$ sudo lilo -M /dev/sda1 mbr
sudo: lilo: command not found
ubuntu@ubuntu:~$ 

It may just be that my Live CD is two years old. :/ I'm going to go download a new one.

---

### Post by oldfred on 2011-04-04
Since you are on the liveCD you should not run the sudo apt-get update, if in a working install then you should run it first.

You also need to enable universe for downloads, if not enabled. Then you should be able to download lilo and install it.

then run the last two commands rubi1200 gave you.

sudo apt-get install lilo 
sudo lilo -M /dev/sda mbr

You will get error messages about the rest of lilo missing, but we are not using lilo but windows in the partition boot sector. So ignore those errors.

---

### Post by burkhardt on 2011-04-04
Okay I made and am running on an Ubuntu Live 10.10 cd now, I just tried both your methods Oldfred and Rubi, but I am still getting the same error message as posted before:

ubuntu@ubuntu:~$ sudo apt-get install lilo
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
sudo: lilo: command not found
ubuntu@ubuntu:~$

---

### Post by oldfred on 2011-04-04
Do you still have synaptic open at the same time? You cannot have synaptic open as it lock things, at the same time you run command line.

---

### Post by burkhardt on 2011-04-04
Thank You! Thank You! Thank You! It worked, I had been leaving synaptic up in the background thinking it was needed. My system is now working better than before. Thank you so much to both of you!

---

### Post by Rubi1200 on 2011-04-05
Excellent! I am really pleased you got it sorted out in the end :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

