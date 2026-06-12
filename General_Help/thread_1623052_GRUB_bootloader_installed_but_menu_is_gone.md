---
title: "GRUB bootloader installed but menu is gone"
date: 2010-11-16
forum: General Help
---

### Post by the basics on 2010-11-16
:confused:Hello,
When I open the machine it posts to the GRUB terminal, which I am lead to believe means that 
GRUB is installed.
 
I used the Ubuntu 8.04 disc and went to its terminal, got the grub prompt [sudo grub] and 
followed the couple of lines to setup Grub on (hd0,0), [hda, 1] which I confirmed (through 
sudo Fdisk /dev/hda ) was the location of GRUB.
(Just followed the instructions as given by someone who knows what they're doing)
I used my GParted CD to check the partitions and on GParted GRUB is marked as hda,a. The 
flag shows it is an active boot, as does the * next to GRUB on the "Ubuntu terminal>GRUB" 
show.
I am getting the following message:
"ubuntu@ubuntu:/$ sudo grub
grub> root (hd0,0)
grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... no
Checking if "/grub/stage1" exists... no
Error 15: File not found ."
 
I typed
"
root ([TAB]
to see what drives are available. 
then 
find (hd0,0)/grub/stage1
It said stage 1 does not exist"
 
I did the:
root (hd0,0)
setup (hd0) -- again. no errors But, still nothing.
 
(Someone on an old thead posted;
"I ran fsck on the partitions which I had restored with g4l and they showed clean. I then 
mounted partitions on the drive and poked about. I was able to navigate around the / and 
/home partitions (sda1 and sda2) with no problem. The stage1 file appeared to be where it 
was supposed to be"
I don't understand what he did, so I can't follow it.) 
 
I have XP32 on hd0,1, XP64 on hd0,2 and Ubuntu on hdo,6.
The machine was working properly and then it was stored for a year.
It works fine with the live cd and I have the GRUB shell, which,as I said, lands me at the 
GRUB prompt.
I am assuming that the kernel is not mounted ? (whatever that entails, as one GRUB error 
message on the machine GRUB terminal said I had to install kernel before.....
Anyway, I remember that installling the three systems was quite grueling, as I first 
installed 32, then changed the boot ini file, and then installed 64 and changed the boot ini 
file there, and then installed ubuntu - with great trepidation- as it seems to want to 
partition my discs, which I had pre-partitiond with GParted.
If I knew how to reinstall GRUB outside of the Ubuntu CD, I guess I could copy the GRUB text 
and the Windows text from another machine that has the same basic install, and redo it. Last 
time I beleive I usd the Ubuntu installer that has Grub included.
Any help would be appreciated.
I will enter a second post about another machine, which also has a triple boot, and which 
posts to the GRUB menu, but in order to boot to either XP or XP 64, I have to use the 
terminal, go to E and remove the line that says "Default"...( although "default" is 
contained in the boot menu for xp and xp64 on my other machine that is still functioning 
properly. All were done at the same time. All were stored for the same length of time.)
I then hit the key for boot and I'm in; but I have to do this each time as the edit is 
temporary. I assume that limited bash editing means it's temporary?
 
Anyway, I will have to access GRUB through a cd with an appropriate program that will allow 
me to pemanently edit out those lines.
I will deal with this after I get the first machine up and running.
Dorian

---

### Post by Hippytaff on 2010-11-16
if you can run a LiveCD or USB and run this script
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Then post the results.txt (which should appear on your desktop)
It will provide some useful info for people to help diagnose the problem :-)
You might need to fix/reinstall grub :-)

---

