---
title: "I can't boot into Ubuntu"
date: 2011-01-29
forum: General Help
---

### Post by tibby.mckenzie@bigpond.co on 2011-01-29
I am running Ubuntu 10.10 on a small partition on my PC.  I was creating a dvd from from some mp4 files from my daughter's camera and the computer just went blank.  When I tried to reboot it just came up with please insert boot media and press enter.  I had my original Ubuntu set up CD handy so whacked that into the cd drive and got to the install page.  I just said to try Ubuntu thinking that my hard disk drive obviously had become too full and I needed to delete some files and could do it through the boot up version of the program.  Well I can get into Ubuntu and obviously can access the internet (that's how I can send this) but I can't see the directory where my files are kept so I can delete some.  I am fairly new to Ubuntu and was hoping that someone could give me a step by step procedure to be able to mount the drive with my files on it so I can delete some and get things working again.  Please help.

---

### Post by mrhhug on 2011-01-29
10.10 should auto mount the most common filesystem, what does gparted tell you? does it show all the partitions being in good health?

```
gksudo gparted
```

---

### Post by Rubi1200 on 2011-01-29
Hi and welcome to the forums tibby :-)

First things first, go to Applications > Accessories > Terminal on the LiveCD and run these diagnostic command:

```
sudo fdisk -lu
```

Copy/paste the output and post it back here.

Next, go to System > Administration > GParted and post a screenshot of what it sees with your drives.

Once we see this, then we can move ahead with the next steps.

---

### Post by tibby.mckenzie@bigpond.co on 2011-01-29
This is what happened:

ubuntu@ubuntu:~$ sudo fdisk -lu
ubuntu@ubuntu:~$

---

### Post by tibby.mckenzie@bigpond.co on 2011-01-29
When I did the 
sudo gparted

The partition manager thingy came up but it was all dimmed and I couldn't click on anything.

---

### Post by Rubi1200 on 2011-01-29
The command is ```
gksudo gparted
``` because it is a graphical application.

Try again please.

Also, take a look at System > Administration > Disk Utility and see what you find.

Look at the health of the drive and whether your partitions are listed.

---

### Post by tibby.mckenzie@bigpond.co on 2011-01-29
ubuntu@ubuntu:~$ gksudo gparted
======================
libparted : 2.3
======================
ubuntu@ubuntu:~$

---

### Post by tibby.mckenzie@bigpond.co on 2011-01-29
I don't think my partitions are listed on the disk utility program.  I had this problem a week ago as well and then I was able to access the home directory after booting up with the install disc, but it doesn't want to play that way today.

---

### Post by Rubi1200 on 2011-01-29
This is not looking good, but don't give up yet.

This is what I suggest now:

Download, burn to CD, and run as a LiveCD a distro called Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

Unlike Ubuntu, and some other distros, Slax does not try and auto-mount partitions (which may be part of the problem here).

Once booted, try the```
 fdisk -lu
``` command again in the terminal on Slax.

Note, you do not need to preface the command with sudo since you will have a root prompt already.

---

### Post by amsterdamharu on 2011-01-29
Did you forgot sudo when you gave the fdisk command:
```
[COLOR=Red]sudo[/COLOR] fdisk -lu
```

Fdisk listing nothing means that you have no harddisks in there or that they are broken/loose power cable/....

Could you run the boot info script from a live CD?
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Copy it to your Desktop (it usually is in Downloads).
Run the following commands:
```
cd ~/Desktop
sudo bash boot_info_script*
```
To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
There should be a file on your Desktop named RESULTS.txt please post the content of this file here too using &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by tibby.mckenzie@bigpond.co on 2011-01-29
/home/ubuntu/Desktop/Screenshot-Disk Utility.png

---

### Post by Rubi1200 on 2011-01-29
> **tibby.mckenzie@bigpond.co said:**
> /home/ubuntu/Desktop/Screenshot-Disk Utility.png
I don't see the screenshot?

amsterdamharu also made a good point; have you checked all your power cables to make sure nothing came loose/got damaged?

---

### Post by runeh76 on 2011-01-29
Hi try this:

Start computer and press **ctrl+alt+f1** (u should get Terminal).
IF u get Terminal, type ```
sudo apt-get install gparted
```
Run Gparted ```
sudo gparted
```

Hope this helps.

---

### Post by tibby.mckenzie@bigpond.co on 2011-01-29
:lolflag:
Legends!!!!!!!!  Success!!!!!!!!!  Yes the hard disk had become unplugged.  I have been having to thump the CD drive to get my disks in and out and I suppose must have thumped it one time too many!!!!!!!!!  Problem solved and thanks to everyone for their support, assistance and advice and for simply just being there for me when I needed you!

---

### Post by Nixarter on 2011-01-29
Be very careful with that.   Disconnecting power to a live drive is like playing Russian roulette.  You've been lucky enough to get away with it once, don't count on it again...  They typically work their way out over time when they aren't tight enough... and they generally aren't replaceable (as they are connected to your power supply).  Just check it periodically (weekly, perhaps) to make sure that it is securely connected.

---

### Post by Rubi1200 on 2011-01-30
> **tibby.mckenzie@bigpond.co said:**
> :lolflag:
Legends!!!!!!!!  Success!!!!!!!!!  Yes the hard disk had become unplugged.  I have been having to thump the CD drive to get my disks in and out and I suppose must have thumped it one time too many!!!!!!!!!  Problem solved and thanks to everyone for their support, assistance and advice and for simply just being there for me when I needed you!
Excellent! Glad you got it sorted out :-)

Thanks too to amsterdamharu.

Good advice as well from Nixarter.

---

### Post by runeh76 on 2011-01-30
:guitar:

---

