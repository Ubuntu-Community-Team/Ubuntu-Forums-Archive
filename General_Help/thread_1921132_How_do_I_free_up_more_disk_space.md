---
title: "How do I free up more disk space?"
date: 2012-02-06
forum: General Help
---

### Post by Welly Wu on 2012-02-06
I keep getting warnings from Disk Utility that I have less than 71.00 megabytes of available disk space on my computer. I used the alternative installation CD to install Ubuntu 10.04.3 64 bit LTS and I used the Update Software feature to upgrade to Ubuntu 11.10 64 bit by going through the upgrade process for 10.10, 11.04, and then 11.10 64 bit.

I opened up the BASH terminal and I typed in these commands:

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

I also used the Computer Janitor to clean up unused packages.

What else can I do to free up more disk space on my / root folder?

I use full disk encryption using LUKS/LVM with AES-CBC mode 256 bits and SHA-256 hash algorithm. Here is how I setup my partitions:

250 megabytes: /boot folder
10.00 gigabytes: / root folder
129.00 gigabytes: /home folder

---

### Post by doobrie on 2012-02-06
Which partition is running out of space?

---

### Post by Elfy on 2012-02-06
Please run and paste the output of 

df -h

I'd hazard a guess and say you'll need to free some of /home and add it to /

Have a look at this thread too - [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
The size of / is going to depend on what you have installed - possible that you have some large logs in /var as well.

---

### Post by dragonfly41 on 2012-02-06
Recently I had the same problem with ubuntu 10.10  (my /root was also 10GB) and I ended up having to resize /root and /home partitions to allow more head room.

Meanwhile try installing **bleachbit** if you can still boot up in ubuntu.

There are some threads around explaining where to clear out trash, cache, logs etc.  e.g. /var/logs/

---

### Post by decrepit on 2012-02-06
empty the trash can????

---

### Post by Welly Wu on 2012-02-06
wellywu@N61JV-X2:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/volumegrp01-volume2
                      9.2G  7.1G  1.7G  82% /
udev                  3.8G   12K  3.8G   1% /dev
tmpfs                 3.9G   12K  3.9G   1% /tmp
tmpfs                 1.6G  916K  1.6G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  3.9G  165M  3.7G   5% /run/shm
/dev/sda1             230M   38M  180M  18% /boot
/dev/mapper/volumegrp01-volume3
                      130G  5.6G  118G   5% /home
/home/wellywu/.Private
                      130G  5.6G  118G   5% /home/wellywu
/dev/mapper/truecrypt1
                      1.4T  945G  361G  73% /media/truecrypt1
/dev/mapper/truecrypt2
                      118G   64G   49G  57% /media/truecrypt2
wellywu@N61JV-X2:~$

---

### Post by Welly Wu on 2012-02-06
I am not getting the Disk Usage popup window telling me that I have less than 71.00 megabytes of available disk space after I performed those commands listed in my original post and I used Computer Janitor. However, please help me to understand if that solved my problem or not. I installed Ubuntu 11.10 64 bit about three weeks ago so I am a new Ubuntu user. I checked out the Ubuntu thread that was posted and I am learning about it right now. It will take me some time to understand it fully.

How does it look now that I posted my df -h output?

How can I avoid seeing disk usage telling me that I am running low on available disk space in the future?

I don't want to resize any partitions. I would rather do another clean custom installation with a 20 gigabyte / root folder using the alternative installation .ISO burned onto a DVD-R disc for the upcoming Ubuntu 12.04 64 bit LTS, but I will do so only if it is absolutely necessary. I don't want to re-install Ubuntu 64 bit from scratch again.

---

### Post by Elfy on 2012-02-06
At the moment you have 1.7Gb of / free and 118Gb of /home free.

Just keep an eye on /

---

### Post by Welly Wu on 2012-05-11
df: `/root/.gvfs': Permission denied
Filesystem                        Size  Used Avail Use% Mounted on
/dev/mapper/volumegrp01-volume02   14G   13G  417M  97% /
udev                              3.8G  4.0K  3.8G   1% /dev
tmpfs                             1.6G  1.6M  1.6G   1% /run
none                              5.0M     0  5.0M   0% /run/lock
none                              3.8G  808K  3.8G   1% /run/shm
/dev/sda1                         476M   81M  371M  18% /boot
/dev/mapper/volumegrp01-volume03  127G  8.1G  113G   7% /home
/home/wellywu/.Private            127G  8.1G  113G   7% /home/wellywu
/dev/mapper/truecrypt1            1.4T  562G  765G  43% /media/truecrypt1
/dev/mapper/truecrypt3            466G   55G  388G  13% /media/truecrypt3
/dev/mapper/truecrypt4            2.8T   42G  2.6T   2% /media/truecrypt4
/dev/mapper/truecrypt6            1.9T  568G  1.2T  33% /media/truecrypt6
/dev/mapper/truecrypt5            9.7M  2.6M  6.6M  29% /media/truecrypt5
wellywu@N61JV-X2:~$

According to this, I have 417 MB of free space on my /root partition. I re-installed Ubuntu 12.04 64 bit LTS three days ago.

How do I free up more space on my /root partition?

---

### Post by mastablasta on 2012-05-11
> **Welly Wu said:**
>  
How do I free up more space on my /root partition?
 
unintsall the progs you don't need or increase the size of root to 12gb or more.

---

### Post by Welly Wu on 2012-05-11
wellywu@N61JV-X2:~$ df -h df: `/root/.gvfs': Permission denied Filesystem                        Size  Used Avail Use% Mounted on /dev/mapper/volumegrp01-volume02   49G  6.7G   40G  15% / udev                              3.8G  4.0K  3.8G   1% /dev tmpfs                             1.6G  1.2M  1.6G   1% /run none                              5.0M     0  5.0M   0% /run/lock none                              3.8G  148K  3.8G   1% /run/shm /dev/sda1                         951M   89M  815M  10% /boot /dev/mapper/volumegrp01-volume03   92G  6.0G   82G   7% /home /home/wellywu/.Private             92G  6.0G   82G   7% /home/wellywu /dev/mapper/truecrypt1            1.4T  562G  765G  43% /media/truecrypt1 /dev/mapper/truecrypt3            466G   64G  379G  15% /media/truecrypt3 /dev/mapper/truecrypt4            2.8T   42G  2.6T   2% /media/truecrypt4 /dev/mapper/truecrypt5            9.7M  2.6M  6.6M  29% /media/truecrypt5 /dev/mapper/truecrypt6            1.9T  568G  1.2T  33% /media/truecrypt6 wellywu@N61JV-X2:~$

I just finished re-installing Ubuntu 12.04 64 bit LTS using the Alternative Install .ISO on a CD-R disc. I set my /swap space to 8 GB. I set my /root partition to 52 GB. I set my /home partition to 98 GB. I have an Intel 2nd Generation MLC NAND FLASH X25-M 160 GB Solid State Drive and Crucial 8.00 dual-channel DDR3 PC-8500 SDRAM. My computer is an ASUS N61JV-X2 notebook PC.  This solves my problem for a long time. I hope that I can continue to stick with Ubuntu 12.04 64 bit LTS until late April 2014. I have 87.0 GB of available disk space on my /home partition now.

---

### Post by Welly Wu on 2012-05-26
wellywu@N61JV-X2:~$ df -h
Filesystem                        Size  Used Avail Use% Mounted on
/dev/mapper/volumegrp01-volume02   49G   34G   13G  73% /
udev                              3.8G  4.0K  3.8G   1% /dev
tmpfs                             1.6G  1.4M  1.6G   1% /run
none                              5.0M  8.0K  5.0M   1% /run/lock
none                              3.8G  1.9M  3.8G   1% /run/shm
/dev/sda1                         951M  121M  783M  14% /boot
/dev/mapper/volumegrp01-volume03   92G   14G   74G  16% /home
/home/wellywu/.Private             92G   14G   74G  16% /home/wellywu
/dev/sdb1                         3.1G  112M  3.0G   4% /media/Kindle
/dev/mapper/truecrypt1            1.4T  605G  722G  46% /media/truecrypt1
/dev/mapper/truecrypt3             98M   93M  508K 100% /media/truecrypt3
/dev/mapper/truecrypt4            2.8T   75G  2.6T   3% /media/truecrypt4
/dev/mapper/truecrypt5            2.8T   42G  2.6T   2% /media/truecrypt5
/dev/mapper/truecrypt6            1.9T  613G  1.2T  35% /media/truecrypt6
wellywu@N61JV-X2:~$

---

### Post by Welly Wu on 2012-05-26
As you can see, my /dev/mapper/volumegrp01-volume02 49G 34G 13G 73% / is my /root partition. I installed Ubuntu 12.04 64 bit Long Term Support using the Alternative Install .ISO on a 700 MB CD-R disc. I specified a 52 GB /root partition and I used LUKS/LVM with the Serpent cipher in CBC ESSIV SHA-256 mode of operation at 256 bits using SHA-512 hash algorithm. I also have a /dev/mapper/volumegrp-01-volume01 which is 8.00 GB and set as my /swap partition. The /dev/mapper/volumegrp01-volume03 is my /home partition and I set it as 98 GB.

I am slowly running out of space on my /root partition. I tried Bleachbit and I also tried sudo apt-get clean, sudo apt-get autoclean, and sudo apt-get autoremove. Nothing works. I can not uninstall any software packages because I need all of them.

How do I clear out my logs to save space?

What else can I do to clear out space on my /root partition?

---

### Post by Welly Wu on 2012-06-03
wellywu@N61JV-X2:~$ df -h
Filesystem                        Size  Used Avail Use% Mounted on
/dev/mapper/volumegrp01-volume02   49G   46G  495M  99% /
udev                              3.8G  4.0K  3.8G   1% /dev
tmpfs                             1.6G  1.2M  1.6G   1% /run
none                              5.0M  8.0K  5.0M   1% /run/lock
none                              3.8G  848K  3.8G   1% /run/shm
/dev/sda1                         951M  121M  783M  14% /boot
/dev/mapper/volumegrp01-volume03   92G   29G   60G  33% /home
/home/wellywu/.Private             92G   29G   60G  33% /home/wellywu
/dev/mapper/truecrypt1            1.9T  625G  1.2T  36% /media/truecrypt1
wellywu@N61JV-X2:~$

Earlier this morning, I had 11.00 GB of free space on my /dev/mapper/volumegrp01-volume02. I recently signed up for WiTopia VPN and I installed network-manager-vpnc and network-manager-openvas. I also installed OSSEC HIDS and it keeps giving me level 2, 7, and 10 alerts to my Google Gmail address.

I am looking at Disk Usage and it tells me that my /var and /usr take up 1.6 and 10.0 GB respectively.

This always happens to me. I just deleted some logs in /var/log and it did not seem to help that much. I do not want to re-install Ubuntu 12.04 64 bit Long Term Support every few weeks of usage.

What can I do to clear some unnecessary disk space?

---

### Post by Cheesemill on 2012-06-03
You need to find out what is taking up 46GB of space on your / partition. That is an excessive amount of used space for a system where you have a separate home (I've never known my / to take more than 10GB).

Change directory into / by doing 'cd /' and then run the following command:
```
sudo du -h --max-depth=1
```That will give you an outlook on which directory is using up the most space, you can then cd into that directory and run the same command again to drill down into your directories until you find out what is using up all of your space.


  Also if you post the results of any commands inbetween [noparse]```
 
```[/noparse] tags it will make your posts far easier for us to read :)

---

### Post by Welly Wu on 2012-06-03
```
wellywu@N61JV-X2:~$ sudo du -h --max-depth=1
[sudo] password for wellywu: 
Sorry, try again.
[sudo] password for wellywu: 
24K	./.vidalia
85M	./.rpmdb
4.0K	./Public
12K	./.ike
456M	./.shotwell
2.4G	./Pictures
1.6M	./.launchpadlib
1.4M	./.liferea_1.8
858M	./.google
301M	./.config
1.9G	./Ubuntu One
3.5M	./.gconf
16K	./.fluendo-dvd
2.0M	./.adobe
2.0M	./Welly-Wu-Documents
12K	./.hplip
7.4M	./US National Security Agency
16K	./Downloads
48M	./Defense Information Systems Agency
24K	./.qt
du: cannot access `./.gvfs': Permission denied
184K	./Google Accounts Backup Codes
18M	./Dropbox
20K	./.dbus
4.0K	./Templates
16K	./.mono
6.9M	./Documents
64K	./.gnome2
1.2G	./Ubuntu 64 bit Software Repository
649M	./KEYS
4.0K	./.icons
508M	./.local
186M	./.xbmc
52K	./Tripwire
100K	./TorVPN
4.0K	./Temp
52K	./PayPal
249M	./.wine
139M	./.mozilla
428K	./.gnupg
544K	./.compiz-1
164K	./.xchat2
2.6G	./Magazines
28K	./Desktop
60K	./.gnucash
6.4M	./KeePass2_latest_version
20K	./.mission-control
4.0K	./Pictures - Transformer TF101
580K	./.kde
28K	./.appdata
4.0K	./.ssh
2.9M	./vmware
76K	./.pki
28K	./.TrueCrypt
25M	./.opera
391M	./.thunderbird
6.6M	./LastPass_Premium
2.1G	./.cache
856K	./SovereignBank
304K	./.easytag
568K	./.Skype
1.4M	./.lastpass
4.0K	./.vmware
14M	./.dvdcss
928K	./.gstreamer-0.10
13M	./.dropbox
47M	./.dropbox-dist
136K	./.VirtualBox
21M	./Evolution
4.0K	./.themes
28M	./Medical Records
4.0K	./.gnome2_private
6.4M	./.thumbnails
420K	./.java
492K	./.macromedia
836K	./.purple
96K	./.pulse
4.0K	./Videos
4.0K	./Music
5.8M	./KeePass2
1.5M	./.fontconfig
616M	./ASUS N61JV Device Drivers for Microsoft Windows 7 64 bit
13G	./VirtualBox VMs
156K	./.nv
90M	./Calibre Library
45M	./Integrit
27G	.
wellywu@N61JV-X2:~$
```

---

### Post by Welly Wu on 2012-06-03
Work with me here.

What should I target on this list to free up disk space?

It looks like most of the familiar data is on my /home partition which has 63.40 GB of free space which is not my problem.

I can not understand how I had 11.00 GB of free space on my /root partition early this morning and I now have less than 500 MB of free space on my /root partition several hours later.

What the hell is taking up that extra 11.00 GB of data space?

---

### Post by Welly Wu on 2012-06-03
This is my /root partition:

wellywu@N61JV-X2:~$ cd /
wellywu@N61JV-X2:/$ sudo du -h --max-depth=1
[sudo] password for wellywu: 
0	./sys
3.3M	./lib32
12M	./sbin
16K	./lost+found
25M	./etc
4.0K	./srv
9.6M	./bin
543M	./lib
4.0K	./lib64
1.7G	./media
4.0K	./dev
1.8G	./var
1.3M	./run
4.0K	./selinux
4.0K	./mnt
9.1G	./usr
du: cannot access `./home/wellywu/.gvfs': Permission denied
54G	./home
du: cannot access `./proc/3863/task/3863/fdinfo/10': No such file or directory
du: cannot access `./proc/8992/task/8992/fd/4': No such file or directory
du: cannot access `./proc/8992/task/8992/fdinfo/4': No such file or directory
du: cannot access `./proc/8992/fd/4': No such file or directory
du: cannot access `./proc/8992/fdinfo/4': No such file or directory
0	./proc
91M	./boot
9.7M	./root
596M	./opt
1.2M	./tmp
68G	.
wellywu@N61JV-X2:/$

---

### Post by Welly Wu on 2012-06-03
I do not want to re-install Ubuntu 12.04 64 bit Long Term Support from scratch again.

I can not answer specific questions about obviously confidential data that I posted in any detail like my job.

In my /root partition, it says that my /media/, /var/, /usr/ take up more than 1.00 GB. I looked at Disk Usage Analyzer and I see some questionably large folders and files like my CrashPlan software package.

Please help me clear out unnecessary disk space.

---

### Post by uRock on 2012-06-03
Running Bleachbit will clear up a lot of space. Run it as root, then run it as a normal user. It will make you very happy:p If you need help with which boxes to check to preserve passwords, while clearing as much space as possible, then let me know.

---

### Post by Welly Wu on 2012-06-03
I am at Starbucks waiting for my best friend to arrive so that we can do our business together later this afternoon.

I did download and I installed Bleach bit. I ran it as a normal user previously and it cleared out 3.10 GB of free space on my /home partition, but it did not clear up any space on my /root partition. I never ran Bleach bit as root.

In the BASH Terminal, type in sudo su, type in my administrator password then type in bleachbit.

I do not want to clear out saved passwords.

What should I click in Bleach bit as root to clear out disk space?

Is this going to work or not?

---

### Post by Welly Wu on 2012-06-03
I found the two icons in Dash for Bleachbit to run as a normal user which I have already done so once and to run Bleachbit as root which I have never done before and this would be the option that I am primarily looking for since it targets my /root partition.

I will run both tonight overnight. I have an Intel 2nd Generation 2.5" MLC NAND FLASH X25-M 160 gigabyte Solid State Drive so it should be very fast.

---

### Post by uRock on 2012-06-03
I've included a screenshot of Bleachbit(as root) showing up in "Installed Programs" and of what I regularly clean out with Bleachbit(as root). Passwords are only an issue when running as a regular user.

---

### Post by Welly Wu on 2012-06-03
wellywu@N61JV-X2:~$ df -h
Filesystem                        Size  Used Avail Use% Mounted on
/dev/mapper/volumegrp01-volume02   49G   15G   32G  32% /
udev                              3.8G  4.0K  3.8G   1% /dev
tmpfs                             1.6G  1.2M  1.6G   1% /run
none                              5.0M  8.0K  5.0M   1% /run/lock
none                              3.8G  2.1M  3.8G   1% /run/shm
/dev/sda1                         951M  121M  783M  14% /boot
/dev/mapper/volumegrp01-volume03   92G   29G   60G  33% /home
/home/wellywu/.Private             92G   29G   60G  33% /home/wellywu
/dev/mapper/truecrypt1            1.4T  616G  711G  47% /media/truecrypt1
/dev/mapper/truecrypt3            297M   64M  219M  23% /media/truecrypt3
/dev/mapper/truecrypt4            2.8T  104G  2.5T   4% /media/truecrypt4
/dev/mapper/truecrypt5            2.8T   42G  2.6T   2% /media/truecrypt5
/dev/mapper/truecrypt6            1.9T  625G  1.2T  36% /media/truecrypt6
wellywu@N61JV-X2:~$

I have no idea what just happened, but my best friend dropped me off back at my home a few minutes ago from Starbucks. I just unpacked my Microsoft 17" Messenger Bag and I plugged in everything. My ASUS N61JV-X2 notebook PC still runs Ubuntu 12.04 64 bit Long Term Support GNU/Linux. According to this latest df -h output which was done at 19:36:25 PM EST, I have 32.00 GB of available disk space on my /root partition. I did not run Bleachbit as root or normal user yet.

What just happened?

How did I suddenly gain all of that extra available disk space?

The only thing that I did was to delete my truecrypt4 as a destination within my CrashPlan data backup software application. Now, I am backing up the same data from my /home partition onto the truecrypt4 volume which is one of my two identical Seagate FreeAgent GoFlex Desk 3.00 terabyte Super Speed USB 3.0 desktop hard disk drives.

What is going on here?

How did I wind up inadvertently solving my problem?

Again, I did not run Bleachbit as root or normal user at all this entire week including today.

Someone please answer my question.

---

### Post by Welly Wu on 2012-06-05
wellywu@N61JV-X2:~$ df -h
df: `/home/wellywu/.gvfs': Transport endpoint is not connected
Filesystem                        Size  Used Avail Use% Mounted on
/dev/mapper/volumegrp01-volume02   49G   19G   28G  41% /
udev                              3.8G   12K  3.8G   1% /dev
tmpfs                             1.6G  1.5M  1.6G   1% /run
none                              5.0M   16K  5.0M   1% /run/lock
none                              3.8G  4.4M  3.8G   1% /run/shm
/dev/sda1                         951M   64M  840M   7% /boot
/dev/mapper/volumegrp01-volume03   92G   33G   55G  38% /home
/dev/mapper/truecrypt1            1.4T  620G  707G  47% /media/truecrypt1
/dev/mapper/truecrypt3            297M   64M  219M  23% /media/truecrypt3
/dev/mapper/truecrypt4            2.8T  156G  2.5T   6% /media/truecrypt4
/dev/mapper/truecrypt5            2.8T   42G  2.6T   2% /media/truecrypt5
/dev/mapper/truecrypt6            1.9T  630G  1.2T  36% /media/truecrypt6
/dev/sdb1                         3.1G  112M  3.0G   4% /media/Kindle
/home/wellywu/.Private             92G   33G   55G  38% /home/wellywu
wellywu@N61JV-X2:~$ 


I just used Ubuntu Tweak to clean out my entire system and it freed up several gigabytes worth of unnecessary data quite fast and easily.

I have not used Bleachbit as root or as a normal user yet. I think that I will do that later today.

I did purchase Humble Indie Bundle V for $8.00 USD so I did download and I installed five PC games for Ubuntu 12.04 64 bit Long Term Support. I also downloaded the .FLAC versions of the five PC game soundtracks, but I saved them to my external Seagate and Western Digital hard disk drives so they are not on my Intel 2nd Generation MLC NAND FLASH X25-M 160 GB Solid State Drive.

I am quite happy. I will report back after using Bleachbit as root and as a normal user. I want to clear up as much unnecessary data as possible.

---

### Post by Welly Wu on 2012-06-06
wellywu@N61JV-X2:~$ df -h
Filesystem                        Size  Used Avail Use% Mounted on
/dev/mapper/volumegrp01-volume02   49G   17G   30G  36% /
udev                              3.8G  4.0K  3.8G   1% /dev
tmpfs                             1.6G  1.4M  1.6G   1% /run
none                              5.0M  8.0K  5.0M   1% /run/lock
none                              3.8G  1.8M  3.8G   1% /run/shm
/dev/sda1                         951M   64M  840M   7% /boot
/dev/mapper/volumegrp01-volume03   92G   34G   55G  39% /home
/home/wellywu/.Private             92G   34G   55G  39% /home/wellywu
/dev/sdb1                         3.1G  114M  3.0G   4% /media/Kindle
/dev/mapper/truecrypt1            1.4T  620G  707G  47% /media/truecrypt1
/dev/mapper/truecrypt3            297M   64M  219M  23% /media/truecrypt3
/dev/mapper/truecrypt4            2.8T   60G  2.6T   3% /media/truecrypt4
/dev/mapper/truecrypt5            2.8T   42G  2.6T   2% /media/truecrypt5
/dev/mapper/truecrypt6            1.9T  630G  1.2T  36% /media/truecrypt6
wellywu@N61JV-X2:~$

I got a response from CrashPlan to a support ticket that I opened a while ago. CrashPlan is located at [http://www.crashplan.com](http://www.crashplan.com). They are a data backup company. CrashPlan does not support TrueCrypt. All of my external storage devices use TrueCrypt. When I configured CrashPlan to backup to my external storage devices protected by TrueCrypt, it would make a duplicate copy of my data backups on my /root partition until it was filled up. This would happen all of the time. So, I decided to let CrashPlan backup my /home partition to CrashPlan Central which is one of their data centers located around the world. Now, I have 30.00 GB of available disk space on my /root partition and it is going to stay that way. CrashPlan was the culprit for eating up my disk space on my Intel 2nd Generation X25-M 160 GB SSD. I have finally pinpointed this problem, isolated it, and solved it permanently.

---

### Post by Welly Wu on 2012-06-12
wellywu@N61JV-X2:~$ df -h
df: `/root/.gvfs': Permission denied
Filesystem                        Size  Used Avail Use% Mounted on
/dev/mapper/volumegrp01-volume02   49G   19G   28G  41% /
udev                              3.8G  4.0K  3.8G   1% /dev
tmpfs                             1.6G  1.5M  1.6G   1% /run
none                              5.0M  8.0K  5.0M   1% /run/lock
none                              3.8G  916K  3.8G   1% /run/shm
/dev/sda1                         951M   64M  840M   7% /boot
/dev/mapper/volumegrp01-volume03   92G   40G   48G  46% /home
/home/wellywu/.Private             92G   40G   48G  46% /home/wellywu
/dev/mapper/truecrypt1            1.4T  629G  698G  48% /media/truecrypt1
/dev/mapper/truecrypt3            297M   64M  219M  23% /media/truecrypt3
/dev/mapper/truecrypt4            2.8T   59G  2.6T   3% /media/truecrypt4
/dev/mapper/truecrypt5            2.8T   42G  2.6T   2% /media/truecrypt5
/dev/mapper/truecrypt6            1.9T  639G  1.2T  37% /media/truecrypt6
/dev/mapper/truecrypt2            466G   46G  397G  11% /media/truecrypt2
wellywu@N61JV-X2:~$

I finally ran Bleachbit as root. It cleaned out 1.00 GB of unnecessary junk.

I pinpointed the specific problem that caused my /root partition to get filled up so quickly. It is due to CrashPlan and local backups.

This thread is solved.

---

