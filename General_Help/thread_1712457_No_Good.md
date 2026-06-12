---
title: "No Good"
date: 2011-03-22
forum: General Help
---

### Post by Miykel on 2011-03-22
G'Day;  Guys;  Well Installed Ubuntu on it's own partition, with W& on another, no good, could only boot into Ubuntu, W7 and all other files were accessible fron Ubuntu but no boot loader to boot into W7, tried to repair with Windows disc and command prompt but could not find any other drives, in the end had to use the Ubuntu disk to delete the Ubuntu partition then reinstall W& onto it's original partition, before I deleted the Ubuntu partition Windows could not find the other drives when I tried to install it, got to where you select the drive where you want to instal and there was nothing there, so I could nnot select a drive to intall onto.
   I still have the unallocated space where I want to instal Ubuntu so does anyone have any suggestions as to how,.
         I thought Ubuntu had its own boot loader, grub, to allow you to duel boot.
  Any guidence would be greatly appreciated   ](*,)
  Kind Regards Miykel.
  The Distro is 10.10 btw.

---

### Post by SeijiSensei on 2011-03-22
It's always best to install Windows first and Ubuntu second.  

BTW, that's not the easiest font to read.  How about just sticking with the default?

---

### Post by cookiecloud on 2011-03-22
Here are some useful hints, althought I don't have the time to fix your system, sorry:

1/ Windows can _never_ see Linux partitions, don't ask me why

2/ gParted is your friend

Wish I could help more, but as was said - start with a blank drive, install windows FIRST, and then Ubuntu last, using the default settings it suggests (the latter part about partitioning is, in my experience, the best way to go for the inexperienced, if that does not sound too patronising :))

CC

---

### Post by Miykel on 2011-03-23
G'Day and thanks for the replies;
    Please forgive me for being slow to answer, major drama with Bigpond.
  Sorry about the fonts, I'll use the default in future.
    I have W7 installed first then Ubuntu, but no grub, I have no idea why I had no grub menu, it just booted into ubuntu without any options, any thoughts would be appreciated.
Kind Regards Miykel

---

### Post by Manyette on 2011-03-23
oPlease let me emphasize what has heen said.  Windows WILL overwrite the grub (Unundtu) boot loader.  You MUST install Windows first!  Then Unbunu's GRUB will pick up the other systems on the harddrive, like Windows!

---

### Post by Miykel on 2011-03-24
G'Day guys;    As I said, I already had W7 installed then installed Ubuntu but when it was installed I had no grub or windows boot loader, the PC would only boot into Ubuntu with no options. To reclaim my PC I had to reinstall W7 but I still want to install Ubuntu onto the allocated partition, which is on a seperate HDD, btw. I must have done something wrong when I installed Ubuntu, if I had done it correctly I would have had grub bootloader and thats what I'm asking about, why no Grub when Ubuntu was installed, I dont remember if there is an option during the install to select grub, if there is then I missed it, What I'm basicly seeking suggestions about is no grub.
   Kind Regards Miykel

---

### Post by chrinabuntu on 2011-03-24
Oh, so you have Ubuntu on a separate hard drive? Well then the problem should be in the hard drive settings...master/slave and all that. Someone will surely chime in here on how exactly to do that, but when you have them on separate hard drives and it's not booting the way you want it, you likely have to switch those settings around as to which hard drive it sees first.

---

### Post by howefield on 2011-03-24
When installing Ubuntu, try selecting manual partitioning and you'll get the option of choosing where grub is installed.

---

### Post by Miykel on 2011-03-24
G'day and many thanks;
     I went through the manual menu to delete and format the partition for ubuntu but is there another option where grub is installed??, Grub is my major drama as it didn't install at all last time.
  Kind regards  Miykel

---

### Post by mendhak on 2011-03-24
I don't recall seeing any Grub options during the installer.  What you should do is edit your Grub configuration. 

sudo gedit /etc/default/grub

Then in that file, look for a GRUB_TIMEOUT. If it's 0, that would explain why your machine is booting straight into Ubuntu.  After you change the timeout, you need to run

sudo update grub


There's also a GUI way - from Synaptic, get 'startupmanager' and you should be able to change the options there. You can also change the default OS as displayed in Grub.  If you don't see Windows 7 there, then you have another problem...

---

### Post by howefield on 2011-03-24
> **Miykel said:**
> G'day and many thanks;
     I went through the manual menu to delete and format the partition for ubuntu but is there another option where grub is installed??, Grub is my major drama as it didn't install at all last time.
  Kind regards  Miykel

Here are screenshots of the installer options for selecting manual partitioning and secondly for selecting where to install Grub.

---

