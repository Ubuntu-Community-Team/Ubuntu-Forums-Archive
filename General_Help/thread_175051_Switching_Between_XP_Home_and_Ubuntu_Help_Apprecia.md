---
title: "Switching Between XP Home and Ubuntu *Help Appreciated!*"
date: 2006-05-12
forum: General Help
---

### Post by zack.peterson on 2006-05-12
Hey. I recently decided to try out Ubuntu Linux when I reformatted my PC about 3 days ago. First, I used DBAN to wipe the Hard Drive. Then, I decided to install Ubuntu before my XP Home Edition (I still wanted XP for things like World of Warcraft). I inserted the Ubuntu installation disk and started setup. I partitioned the hard drive so that it was split 50-50. I installed Ubuntu on the C: partition. I then installed XP on the E: partition (D: is my CD-ROM drive). Then, when I rebooted my comp after the installation of XP was completed, I found that I was not able to decide which OS I wanted to use, Ubuntu or Xp. It automatically started XP. Is there someway that I can override this to give me the ability to switch, or a program or something else? Help is greatly appreciated! Thx. :KS

Zack

---

### Post by Hentai_Jeff on 2006-05-12
reinstall ubuntu and install the grub boot loader. then it'll dual boot right.

---

### Post by BobSongs on 2006-05-12
I'm sure someone'll tell you how to make an adjustment to the boot up system. But for future reference:

Install order

1) Windows (pick any flavour)
2) Ubuntu

That's because Ubuntu is sensitive to the existence of Windows and will set up the boot menu to include this corporate O/S. Windows, on the other hand, will run roughshod over any Linux install. It's their way of saying: "Thanks for paying for Windows." Your Ubuntu install is safe and sound; just hidden.

Welcome to Ubuntu. [Here's the link you're looking for.]("http://www.ubuntuforums.org/showthread.php?t=24113") Read through the thread and don't be hasty. Make sure you understand what they're saying. Check out the various suggestions. They're perhaps a bit short in their descriptions. I may write up a more elaborate "How To" in the near future.

**Edit**: I recall reading through that thread when I first started working with Ubuntu. Good grief! I was worried. I had all sorts of stuff in my Linux drives I didn't want to lose. And that thread was really scary. So, if you can stand to restart your installs, start with Win and end with Lin. If not, go through that link. It's a bit scary, but it should work if you don't panic.

---

### Post by CalvinChile on 2006-05-12
Hi Zack,

As far as I know, you have to install XP first and then install Linux. What I have done is to create a partition for XP and leave the rest free. Then when Linux is installing you choose to use the free space, that way Linux doesn't use the space already allocated to XP. During the final stage, Linux will use GRUB to modify the MBR  to allow the booting from all the OS installed.

Good Luck
Nicolas

---

### Post by Herman on 2006-05-12
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29)

Hello, zack.peterson, try the link above and see if there is something there you like. You don't really need to re-install but you can if you want to. Regards, Herman.

---

### Post by steve.horsley on 2006-05-12
Boot the intaller CD and at the prompt, rather than just booting, type **rescue** and press enter. Get onto your Ubuntu partition (I forget the exact question you are asked) and enter the command **grub-install /dev/hda**. This should install the grub bootloader that will give you a choice.

When you say you partitioned the drive 50:50 and installed Ubuntu on one partition, do you mean that you didn't give it a swap partition? If not, you may be better off deleting the Ubuntu partition, leaving the disk 50% unused, and then running the Ubuntu installer and choosing to use the free disk space. Then the installer will create an ext partition for the system and a swap partition for swap space.

---

### Post by zack.peterson on 2006-05-13
[FONT="Comic Sans MS"][B]Oh, yes!! Thank you all soooooo much! I am typing this from Ubuntu right now. I can't tell you how much I appreciate all of your help and suggestions. I had to reinstall my Ubuntu OS and then it allowed me to install GRUB. Thank you all. 

Zack[/B][/FONT]

---

