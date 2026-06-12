---
title: "install clonezilla on ubuntu"
date: 2009-07-17
forum: General Help
---

### Post by pythonscript on 2009-07-17
How would I go about installing clonezilla on ubuntu? I'm making a custom live cd for diagnostics (kind of like SystemRescueCD, but I'm making a ubuntu-based one as a learning experience :) and I'd like clonezilla to be one utility that I include. All I can find is the live CD version, though, but I'd like to actually install the software under my current ubuntu installation. Any ideas? I don't need any setup for multicasting or anything like that; I'd just like to have the ability to backup my partitions to image files from my custom CD. 

I've had incredibly horrible luck with partimage (google "partimage can't read bitmap block 0 from image" and you'll see the seemingly random nature of the error that always seems to plague me no matter what I do with partimage) so I'm definitely working with just clonezilla. Thanks!

---

### Post by bwitherell on 2009-08-26
Recently I have been toying with the same idea. To install Clonezilla without installing the server parts of it I just took it off of the live CD.

I downloaded the ISO. Mounted the Squashfs file and place the /opt/drbl directory from the mounted squashfs file into the /opt directory on my Ubuntu system. Then I added /opt/drbl:/opt/drbl/bin:/opt/drbl/sbin to my existing PATH setting. I tested creating an image and restoring an image. Both were successful.

Steps:
-download the clonzilla ISO and copy the /live/filesystem.squashfs file from the ISO to your home folder.
-open a terminal and su to root ```
sudo su
```
-make a directory to mount the squash file in ```
mkdir /media/sqfile
```
-mount the squash file ```
mount -t squashfs ./filesystem.squashfs /media/sqfile -o loop
```
-copy the /media/sqfile/opt/drbl directory to your /opt folder
-edit root's .bashrc file to permanently add clonezilla to the PATH environment variable. ```
gedit /root/.bashrc
```
-in the /root/.bashrc type the following line at the bottom of the file. I made this the very last line in the .bashrc file ```
PATH=$PATH:/opt/drbl:/opt/drbl/bin:/opt/drbl/sbin
``` This adds /opt/drbl, /opt/drbl/bin and /opt/drbl/sbin to the PATH variable.
-save and close gedit.
-close the terminal and open a new one
-type ```
sudo su
```
-type ```
clonezilla
``` you should be presented with the clonezilla menu interface inside your terminal window. Make sure you run clonezilla as root.

---

### Post by pythonscript on 2009-08-26
Thanks for the tip! That definitely helps me.

---

### Post by pythonscript on 2009-09-05
Any idea how I could make this into a deb package?

---

### Post by mario0318 on 2009-11-18
Is this really the best tutorial out there to install Clonezilla?

---

### Post by pythonscript on 2009-11-19
> **mario0318 said:**
> Is this really the best tutorial out there to install Clonezilla?

Normally people don't *install* Clonezilla; they just run it from the LiveCD like they do other utilities from SystemRescueCD. I'm thankful to bwitherell for the help.

---

### Post by LukonLinux on 2009-11-28
Thanks for the tutorial.  I followed it, but when I run: 'sudo su' then 'clonezilla' - I get permission denied.  If I try 'sudo clonezilla' - I get command not found...

How do I give myself the proper privileges to run clonezilla from terminal?

Thanks...

---

### Post by tanoloco on 2010-05-03
_**LukonLinux**_: just type ```
sudo chmod 750 /opt/drbl/sbin/* /opt/drbl/bin/*
```from a terminal to have permission to execute clonezilla and files it needs, which must be all owned by root:root of course.

_**bwitherell**_: thank you very much for your tutorial! I've just followed it and now I'll try clonezilla running from a terminal window of my ubuntu!! Exactly what I was searching.. hoping everything go ok. Thanks again! :)

---

### Post by SteffJay on 2010-07-13
> **tanoloco said:**
> _**LukonLinux**_: just type ```
sudo chmod 750 /opt/drbl/sbin/* /opt/drbl/bin/*
```from a terminal to have permission to execute clonezilla and files it needs, which must be all owned by root:root of course.

_**bwitherell**_: thank you very much for your tutorial! I've just followed it and now I'll try clonezilla running from a terminal window of my ubuntu!! Exactly what I was searching.. hoping everything go ok. Thanks again! :)

Nice tut **tanoloco** ;)

---

### Post by AlexanderDGreat on 2010-08-26
Can anyone tell me what clonezilla is good for?

I can backup my system using tar, and rsync, but why use clonezilla? Any particular use for me?

I have a file server in the office.

---

### Post by SteffJay on 2010-08-26
> **AlexanderDGreat said:**
> Can anyone tell me what clonezilla is good for?

I can backup my system using tar, and rsync, but why use clonezilla? Any particular use for me?

I have a file server in the office.

Its just another form of system backup. If the others work fine for you, then no problem.

---

### Post by tanoloco on 2010-09-01
It's not a system backup tool .. it's a cloning tool.

It clones drives and/or partitions.

Cheers
:D

---

### Post by pythonscript on 2010-09-03
> **tanoloco said:**
> It's not a system backup tool .. it's a cloning tool.

It clones drives and/or partitions.

Cheers
:D

Which, in essence, makes it a backup tool, since you can clone a partition to an image and restore the clone back to the same partition, thus imitating backup functionality.

---

### Post by pythonscript on 2010-09-03
On a side note, is there any way this thread can be closed? I've removed my subscription from it, but it seems like it's gotten far off the original topic (which has already been solved, hence why I marked it so).

---

### Post by elperrillo on 2010-12-06
There is a tutoria on how to acomplish both task, I am going to see if I can find it for you. It even shows you how to create executable shortcuts on the desktop to start Clonezilla in multicasting mode, so you do not have to reconfigure the server again for this purpose.

---

### Post by elperrillo on 2011-02-05
You need good tutorials that help you in your process, here are two very good links.

1) [Install clonezilla on Ubuntu]("http://geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/")
2) [Create a Custom Ubuntu Live CD]("http://geekyprojects.com/ubuntu/build-your-own-custom-ubuntu-livecd/") 

Hope this helps you and best of luck with your project.

---

### Post by limp on 2011-05-01
Hi guys,

I followed all the steps bwitherell mentioned so that I run clonezilla from my Ubuntu Live USB stick and I found one thing missing.

When clonezilla starts with the image generation (I used the device-image method), I got errors like that:

```
/opt/drbl/sbin/ocs-functions: line 1010: partimage: command not found
```

or when I selected to used "dd" for generating the image I got:

```
/opt/drbl/sbin/ocs-functions: line 1140: partclone.dd: command not found
```

I figured out that all these tools are contained in the /media/sqfile/usr/sbin directory so the problem solved by adding /media/sqfile/usr/sbin into the PATH variable.

Hope that helped someone...

Regards.

---

### Post by cs_tekkies on 2011-07-03
thank you very much [bwitherell]("http://ubuntuforums.org/member.php?u=277152").... i hope that you will always share you expirience with us regarding ubuntu... you help me a lot... thanks again...

---

### Post by ZioNemo on 2012-01-29
To whom it might concern:

With recent versions of clonezilla you happen to need "pigz".
You can install it in your ubuntu or just copy it from <mount-point>/usr/bin/pigz to /opt/drbl/bin.

I didn't like having clonezilla in my PATH, so I created /usr/local/bin/clonezilla with the following content:
```
#!/bin/bash
PATH=/opt/drbl:/opt/drbl/bin:/opt/drbl/sbin:$PATH
sudo /opt/drbl/sbin/clonezilla
```

HiH
ZioNemo

---

