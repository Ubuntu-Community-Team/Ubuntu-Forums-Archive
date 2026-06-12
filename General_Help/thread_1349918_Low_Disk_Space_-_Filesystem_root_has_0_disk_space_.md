---
title: "Low Disk Space - Filesystem root has 0 disk space remaining"
date: 2009-12-08
forum: General Help
---

### Post by atomicben on 2009-12-08
Every so often I'm getting a message that says that the Filesystem Root has only x disk space remaining. The last couple times it at least reported that some space was left but today it said 0MB remaining which kinda freaked me out.

I've done some searching and found that the error looks like this one:
[http://ubuntuforums.org/showthread.php?t=1330028](http://ubuntuforums.org/showthread.php?t=1330028)

I followed the steps in that guide.  Here are my dh commands and the outputs:[INDENT]$df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G  5.7G   29G  17% /
udev                  502M  312K  501M   1% /dev
none                  502M  140K  502M   1% /dev/shm
none                  502M  500K  501M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
/dev/sdc1             466G  325G  141G  70% /media/500EXT
/dev/sdb1             459G   18G  418G   4% /media/500INT

$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             37848064   5598348  30327140  16% /
udev                    513184       312    512872   1% /dev
none                    513184       152    513032   1% /dev/shm
none                    513184       504    512680   1% /var/run
none                    513184         0    513184   0% /var/lock
none                    513184         0    513184   0% /lib/init/rw
/dev/sdc1            488384000 340642892 147741108  70% /media/500EXT
/dev/sdb1            480719056  18131072 438168784   4% /media/500INT



$ sudo du -csh /*
6.7M    /bin
54M    /boot
0    /cdrom
464K    /dev
22M    /etc
du: cannot access `/home/bdowney/.gvfs': Permission denied
877M    /home
0    /initrd.img
0    /initrd.img.old
397M    /lib
16K    /lost+found
342G    /media
4.0K    /mnt
4.0K    /opt
du: cannot access `/proc/11228/task/11228/fd/3': No such file or directory
du: cannot access `/proc/11228/task/11228/fdinfo/3': No such file or directory
du: cannot access `/proc/11228/fd/3': No such file or directory
du: cannot access `/proc/11228/fdinfo/3': No such file or directory
0    /proc
81M    /root
8.1M    /sbin
4.0K    /selinux
200K    /srv
0    /sys
499M    /tmp
3.5G    /usr
332M    /var
0    /vmlinuz
0    /vmlinuz.old
348G    total

$ sudo du -csh /media/*
325G    /media/500EXT
18G    /media/500INT
0    /media/cdrom
4.0K    /media/cdrom0
0    /media/floppy
4.0K    /media/floppy0
4.0K    /media/iso
342G    total


$ sudo ls -a /root/
.           .debtags        .icedteaplugin    .pulse-cookie
..           Desktop        .kde        .recently-used.xbel
.adobe           .esd_auth    .local        .rnd
.aptitude      .gconf        .macromedia    .sudo_as_admin_successful
.bash_history  .gconfd        .mozilla    .synaptic
.bashrc        .gnome2        .mythtv        .ure
.cache           .gnome2_private    .nautilus    .wapi
.config        .gnupg        .profile    .wine
.dbus           .gstreamer-0.10    .pulse


[/INDENT]I've also attached some screenshots from gparted, the disk usage analyzer and the system monitor file systems tab.  

GParted looks fine.  All the dh commands look fine.  I really don't know what the heck disk usage analayzer is trying to tell me.  

Bottom line:  I have a 40GB HDD (which is my system drive) and 2 500GB HDD (500INT and 500EXT) one is internal (INT) one is external USB2.0 (EXT).

This seems to occur when I record an EXTRA long session (2 hours) using gtk-record mydesktop.  I'm not sure if the error is coming up when recording or when it's processing but the output of record my desktop isn't going to my 40GB it's going to my 500INT drive which is BRAND new, installed on the weekend.  Virtually empty.

This program is using my /tmp directory (on the 40GB system drive) but even so, I've got 30GB free space on the 40GB drive, supposedly.  Recording for 2 hours used to only cost me 1.5GB-2GB.  I'm going to change the tmp directory for gtk-recordMyDesktop and try that out.

In the mean time are there any other suggestions?
Do you see anything that doesn't look right?


Thanks,

Ben

---

### Post by atomicben on 2009-12-08
It wasn't until I was half way through writing my original post that I realized that the tmp directory may be filling up during the recording or processing stage of recordmydesktop.  I probably should have just stopped writing there and tried changing the working folder before posting.  I guess I was hasty.  

I changed the working directory and recorded for about an hour without a problem.  I still can't figure out why 1 or 2 gigs of temp files would fill up my root filesystem.  Is there a limit on the size of the tmp directory?  I'm still kinda new at ubuntu and I'm thinking like  windoze.  If there is a limit, can I increase it?

Thanks.

---

### Post by progone on 2011-01-30
What would I need to do to fix my error that was like your?

---

### Post by progone on 2011-02-01
actually the problem started up once again a few days later.   So where do I begin.

---

### Post by atomicben on 2011-02-02
Sorry but I can barely remember having this issue.  I have no idea what I did to fix it over a year ago.

---

### Post by kenkaku on 2011-06-05
I had this problem too. This is the topic which came up when I searched for a solution; so I'll post what seems to have worked for me.

It turned out that my /var/log directory was being filled up with a couple of logs that decided to go into the GB range. :-/
So, I backed them up to a different device and deleted them. I had to use sudo rm "filename" (since there were tarred backups, appending a .* to the end of the filename helped).

---

### Post by Digital_Man on 2012-05-17
I had the same problem on 12.04 Precise, 64bit. Doing a restart didn't solve it, but doing a full shutdown and then turning the machine on again did.

---

### Post by ChadMMc on 2012-05-17
I have had that problem only occur when I had tried using Devede.  It would give an error and say low disk space? (with the question mark) and then give a mencoder error.  I am running 12.04 64-bit and have a terabyte home partition (and 500gb still open).  Did not have to reboot or anything, so not sure what it was that was causing it, except possibly the mencoder error (which might be coded in such a way to say the disk space is low or somesuch).

---

