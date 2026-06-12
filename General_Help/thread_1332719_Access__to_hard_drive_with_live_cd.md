---
title: "Access  to hard drive with live cd"
date: 2009-11-20
forum: General Help
---

### Post by leehamer on 2009-11-20
Is there a way I can use my livecd (Ubuntu 9.10) to access my hard drive and change my xorg.config for another one I have on my hard drive, I connected an LCD screen and it has killed it... 

I have a copy of my xorg.config saved on my hard drive but I cant work out how to swap them.

I saved the xorg.config file on the desktop of my installation

---

### Post by sisco311 on 2009-11-20
Reboot the computer and select Recovery Mode from the grub menu.

You may have to press the Escape(grub) or Shift(grub2) key during bootup in order to see the menu.

Wait for all the boot-up processes to finish.

Select Drop to root shell prompt option from the Recovery Mode menu.

restore the file:
```
cp /home/**username**/Desktop/xorg.conf /etc/X11/xorg.conf
```

replace **username** with your login name.

type:
```
exit
```
and choose to resume a normal boot.


Or boot the LiveCD. 

[list]
[*] open the file manager as root:
press Alt+F2 and run:
```
gksu nautilus
```
[*] mount the partition 

[*] copy the backup file in the partition's /etc/X11 directory.
[/list]

Be careful!

or from the terminal:
```
sudo cp /media/<mountpoint>/home/<username>/Desktop/xorg.conf /media/<mountpoint>/etc/X11/xorg.conf
```

replace <mountpoint> with the actual mount point and <username> with your login name.

NOTE: use the file manager to mount the partition
NOTE: you can drag a file in the terminal to get the full path to it ;)

---

### Post by Sin@Sin-Sacrifice on 2009-11-20
Yeah for me it's ```
sudo mkdir /media/ubuntu
sudo mount /dev/sda2 /media/ubuntu
cd /media/ubuntu/etc/X11
sudo mv xorg.conf.backup xorg.conf
```
Just change the /ubuntu to whatever and /dev/sda2 to your drive.

---

### Post by leehamer on 2009-11-20
cheers I will give them a try :D

---

### Post by apaulsalerno on 2009-11-20
I have a similar problem, I just loaded with the wubi installer, and I am trying to open up a file that was created and saved in the original windows environment but I can not get to the c drive. When I open  a file in Open Office no computer is listed, and outside of OO if I look at my computer from the places menu there are only the DVD drive and the file system listed, but no c: drive. Is there a way to access my old windows files from within ubuntu?

---

### Post by sisco311 on 2009-11-20
> **apaulsalerno said:**
> I have a similar problem, I just loaded with the wubi installer, and I am trying to open up a file that was created and saved in the original windows environment but I can not get to the c drive. When I open  a file in Open Office no computer is listed, and outside of OO if I look at my computer from the places menu there are only the DVD drive and the file system listed, but no c: drive. Is there a way to access my old windows files from within ubuntu?

*The Windows partition where you installed Wubi is available as /host within Ubuntu (places > computer > file system > host) All the other partitions will be available under places > removable media*

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

host is a directory in the root ("/") of the file system. Your home directory is in /home/username, the root "/" directory is similar to the C:\ directory in Windows. 

EDIT:

Oh, and welcome to the forums!

Next time you have an issue, please start a new thread in the [Absolute Beginners Talk]("http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=326") (or in the appropriate) sub-forum. Thanks.

---

### Post by leehamer on 2009-11-21
Thank you very much for your help, I have got it working fine again now :D

---

### Post by sisco311 on 2009-11-21
> **leehamer said:**
> Thank you very much for your help, I have got it working fine again now :D

Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

