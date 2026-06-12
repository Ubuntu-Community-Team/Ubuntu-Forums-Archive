---
title: "Grub Splash Question"
date: 2011-12-14
forum: General Help
---

### Post by Mizpa on 2011-12-14
I have Kubuntu 11.04 installed. Just before I installed Kubuntu, I had installed a live CD of Linux Mint, just to see if I would like it. My question is this: When I installed Kubuntu, it retained the Mint Grub Splash Screen background, but updated it to offer Ubuntu instead of Mint! Is this a normal thing with Ubuntu/Mint installs? I'm not complaining, it's really only a minor annoyance, no big deal, just wondering. 

If it isn't normal, is there a way of changing the splash screen so that it won't display the Mint background? Thanks:confused:

---

### Post by seawolf167 on 2011-12-14
You can use BURG to customize your boot menu

[BURG ]("https://help.ubuntu.com/community/Burg")Ubuntu Community Documentation
[How to install ]("http://code.google.com/p/burg/wiki/InstallUbuntu")from Burg's code page
[Screenshots]("http://code.google.com/p/burg/wiki/Screenshots")

I'm not sure what exactly the Mint installer does (haven't used it) - but it could have created a separate /boot partition, so when you installed Ubuntu it recognized the /boot partition and overwrote only the necessary entries contained there.

---

### Post by Mizpa on 2011-12-14
Thanks seawolf167, I'll give BURG a look and see if it will answer my questions. I'm new to Ubuntu and Mint, so I don't know exactly what it did!

* Just looked at the BURG page, I'm not interested in trying something new, I'm not a Guru, just a user - I just wanted to see if there was something that would correct whatever went wrong with the grub install ;)

---

### Post by seawolf167 on 2011-12-14
Since I don't know what LinuxMint does regarding Grub, you have two options IMO:

[LIST=1]
[*]Reinstall Grub2 following [this guide]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2") (this probably will not work as the Mint theme carried over from the previous Grub install)
[*]Purge and reinstall Grub2 following [this guide]("http://ubuntuforums.org/showthread.php?t=1581099") (this is essentially guaranteed to work)
[/LIST]
> **Mizpa said:**
> I just wanted to see if there was something that would correct whatever went wrong with the grub install :wink:

As a side note - nothing is wrong with your Grub install since you can  boot up and everything, it is just a aesthetics issue which you could  change manually using BURG which is why I suggested it.

---

### Post by josephmills on 2011-12-14
> **Mizpa said:**
> I have Kubuntu 11.04 installed. Just before I installed Kubuntu, I had installed a live CD of Linux Mint, just to see if I would like it. My question is this: When I installed Kubuntu, it retained the Mint Grub Splash Screen background, but updated it to offer Ubuntu instead of Mint! Is this a normal thing with Ubuntu/Mint installs? I'm not complaining, it's really only a minor annoyance, no big deal, just wondering. 

If it isn't normal, is there a way of changing the splash screen so that it won't display the Mint background? Thanks:confused:

Yes there is not only is BURG awesome but it does work great also. 
when you install a operating system to a new partition of your hard drive it adds grub2 and all its stuff to that partition. now if you would like to see what is booting grub you can do that by entering the command ```
sudo fdisk -l 
``` look for the one with the * next to it that is boot. There is also the command ```
sudo update-grub 
``` this updates all the things that you see in grub like a background that you might have once had. But that fact remains that grub will always boot from well the boot partition. Untill you change where grub is installed. this is a simple thing to do. one open terminal enter ```
sudo fdisk -l 
``` or run ```
sudo update-grub 
``` Here is my update-grub ```
sudo update-grub 
Generating grub.cfg ...
Found background: /usr/share/images/grub/Windbuchencom.tga
Found background image: /usr/share/images/grub/Windbuchencom.tga
Found linux image: /boot/vmlinuz-3.0.0-14-generic
Found initrd image: /boot/initrd.img-3.0.0-14-generic
Found linux image: /boot/vmlinuz-3.0.0-13-generic
Found initrd image: /boot/initrd.img-3.0.0-13-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Debian GNU/Linux (6.0.3) on /dev/sda1
Found Linux Mint Debian Edition (1) on /dev/sda4
Found Ourshare 0.1 (0.1) on /dev/sda7
Found Ubuntu 11.10 (11.10) on /dev/sda9
done
``` now find the one that mint is installed on mine is  /dev/sda4 Now we need to mount that partition. to do this we open are terminal and enter ```
sudo mount /dev/sda4 /mnt/ 
```  now enter ```
cd /mnt/ 
``` then ```
sudo grub-install --root-directory=/mnt /dev/sda
``` then ```
sudo umount /mnt/
``` then reboot. Boot into the MINT and run ```
sudo update-grub
``` then reboot you should be good to go. Hope this helps and have fun.

---

