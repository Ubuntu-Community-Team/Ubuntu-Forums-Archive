---
title: "Ubuntu 10.04 doesn't appear in GRUB - wubi"
date: 2012-07-13
forum: General Help
---

### Post by orestescm76 on 2012-07-13
Today I say: "I'm gonna install Ubuntu on my computer, because goes better than Windows, but, I have inportan files on Windows, I'm gonna do the installation dual with Windows"
I put the Live CD and click on Dual installation with Windows. (Wubi)
Two hours installing.
When its finished, I restart and instead of GRUB appears the Windows Boot Manager with Ubuntu.
I go to Ubuntu and appears GRUB, buuuuut, only Windows, doesn't appear Ubuntu.
Why?

---

### Post by oldfred on 2012-07-13
Welcome to the forums.

Wubi is not a true dual boot but is just a file inside the Windows NTFS partition and uses the Windows boot loader to start. Then it is modified to look just like a regular Ubuntu install.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

So you do get to the grub menu and there is no entry for Ubuntu? Or when you select Ubuntu does it hang and give just a black screen or cursor in upper left corner. If black screen issue it probably is a video driver issue.

From a liveCD run this.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

If you do not have the liveCD:
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by orestescm76 on 2012-07-13
Yea, in GRUB, there is no entry for Ubuntu.

---

### Post by oldfred on 2012-07-13
I do not know wubi. Edited title to add wubi, so those who know wubi better may respond.

This has many fixes:

how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by YannBuntu on 2012-07-13
Hello, and welcome among us :)

> **orestescm76 said:**
> I have important files on Windows

You should first backup these files on an external device (USB disk or DVDs..).
If you can't boot Windows, you can boot an Ubuntu CD, choose "Try Ubuntu", open a file browser to access and backup the documents (if you have a permission problem, open a terminal and type "gksudo nautilus").

---

### Post by orestescm76 on 2012-07-13
> **YannBuntu said:**
> Hello, and welcome among us :)



You should first backup these files on an external device (USB disk or DVDs..).
If you can't boot Windows, you can boot an Ubuntu CD, choose "Try Ubuntu", open a file browser to access and backup the documents (if you have a permission problem, open a terminal and type "gksudo nautilus").

Windows boots fine.

---

### Post by orestescm76 on 2012-07-13
> **oldfred said:**
> I do not know wubi. Edited title to add wubi, so those who know wubi better may respond.

This has many fixes:

how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

I'il try that. Thanks!

---

### Post by YannBuntu on 2012-07-13
If I were you, I wouldn't bother trying to repair Wubi as you have no documents in it.
I would simply install Ubuntu the standard way (outside Windows, see [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) )

---

### Post by orestescm76 on 2012-07-14
> **YannBuntu said:**
> If I were you, I wouldn't bother trying to repair Wubi as you have no documents in it.
I would simply install Ubuntu the standard way (outside Windows, see [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) )

OK, I'il install Ubuntu in another partition.

---

### Post by orestescm76 on 2012-07-14
> **orestescm76 said:**
> OK, I'il install Ubuntu in another partition.
It's solved, i'm on Ubuntu.
It goes very fast.
But, i have 1 more problem.
I need the drivers for Sis VGA to choose Visual Effects and screen resolution.

---

### Post by oldfred on 2012-07-14
It should automatically install the driver you need. If system is just VGA (and old) you may not get the full performance from the gui. If RAM is 512MB or less a more lightweight version like Lubuntu ma be better.

#To see video:
sudo lshw | grep -A 11 display
#Resolution:
xwininfo -root

#list of recommended drivers:
jockey-text -l
#Install a driver:
sudo jockey-text -e <driver>

---

### Post by orestescm76 on 2012-07-14
> **oldfred said:**
> It should automatically install the driver you need. If system is just VGA (and old) you may not get the full performance from the gui. If RAM is 512MB or less a more lightweight version like Lubuntu ma be better.

#To see video:
sudo lshw | grep -A 11 display
#Resolution:
xwininfo -root

#list of recommended drivers:
jockey-text -l
#Install a driver:
sudo jockey-text -e <driver>

I don't know very much, but I'il try that.
Thank you very much!!!!! :p

---

### Post by orestescm76 on 2012-07-14
> **orestescm76 said:**
> I don't know very much, but I'il try that.
Thank you very much!!!!! :p

Well, i've got the screen resolution, but I can't get the screen effects. :(

---

### Post by orestescm76 on 2012-07-15
Help me with the screen effects! :(

---

### Post by oldfred on 2012-07-15
I am not sure what you mean by screen effects?

Are you getting the login screen and the little icon in the upper right lets you choose some different modes. Often with a limited video card you can only run 2d not 3d mode.

---

### Post by orestescm76 on 2012-07-15
Sorry, I mean Desktop Effects.

---

### Post by orestescm76 on 2012-07-15
I'm gonna update to the new version of Ubuntu (12.04)

---

