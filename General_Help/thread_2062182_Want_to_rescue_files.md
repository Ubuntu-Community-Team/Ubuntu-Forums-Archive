---
title: "Want to rescue files"
date: 2012-09-24
forum: General Help
---

### Post by Jpendragon on 2012-09-24
I don't know how, but my xubuntu partition no longer outputs a signal that my monitor understands. I think I may have had a problem with my internet when I updated a graphics driver or something. But that's not the point because I think it will be easier to reinstall than to try and fix the driver.

However,

I was storing some important files on this partition and I don't want to lose them. When I open up a trial version of xubuntu  to see if I can access them, I can browse the folders that they were  in, but the only ones I can see/copy/cut/move are the files that were  created/downloaded on this partition. If it was moved to this computer  via a flash drive or external harddrive, I don't have read/write  permissions.

How do I rescue them?

---

### Post by jerrrys on 2012-09-24
I would think fixing the driver issue would be easier than reinstalling, but up to you :)

[For permissions]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=partition+read%2Fwrite+permissions&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F")

And maybe a [data partition]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F") would be a good idea in the future.

---

### Post by irv on 2012-09-24
If you are using Thunar for a file manager in Xfce just open a terminal and type:
```
sudo thunar
```
enter your password and you should be able to rescue your files.

---

### Post by alphaamanitin on 2012-09-24
Once you move them you can just take ownship of the files if you are the superuser. chmod command or something like that I think.  I don't need to use it much.

AlphaA

---

### Post by jerrrys on 2012-09-24
> **irv said:**
> If you are using Thunar for a file manager in Xfce just open a terminal and type:
```
sudo thunar
```enter your password and you should be able to rescue your files.

good call irv

gksudo thunar :)

---

### Post by Jpendragon on 2012-09-24
Am I to do this while I'm using the live USB of xubuntu? Because that is the only way I can do anything on linux and be able to use a monitor.

I enter in sudo thunar and I just get a window that opens to browse files that has a red band saying "Warning, you are using the root account, you may harm your system." There is no place to enter a password.

Is there perhaps a way to sign in as my username on my computer through the live USB?

---

### Post by irv on 2012-09-25
> **Jpendragon said:**
> Am I to do this while I'm using the live USB of xubuntu? Because that is the only way I can do anything on linux and be able to use a monitor.

I enter in sudo thunar and I just get a window that opens to browse files that has a red band saying "Warning, you are using the root account, you may harm your system." There is no place to enter a password.

Is there perhaps a way to sign in as my username on my computer through the live USB?

When you are running off the live OS there is no password, and yes you have root access so be careful. All you want to do here is copy your files from your old partition to a backup device. This way if you do a clean install or wipe your drive you will have your data files backed up.

---

### Post by Jpendragon on 2012-09-26
Okay, I did that and saved my files.

However, when I reinstalled, GRUB threw a hissy fit and was like "oh my god, I don't know what's going on!" so I tried every combination of reinstalling things like grub and the swap space, ect. Finally I just started from scratch and reinstalled windows. Then I followed [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/) <<this person's instructions on how to get it to dual boot (although I shrunk the windows partition in windows and then added a FAT32 partition in Gparted to be my data partition). But when the installation was over, and it asked to restart my computer, it restarted into Xubuntu, not Windows. 

This is not congruent with my previous experience with all this. I can't run windows now even though the Windows partitions remained untouched (I can see them). I do need both Operating Systems for school though, so if someone could help me with my dual boot issues, that would be lovely. I don't want to have to start yet another thread on here; I feel like I'm crowding the place.


P.S. This time, xubuntu is not pillar-boxed, so some good has come out of this.

---

### Post by jerrrys on 2012-09-26
Glad to hear that progress has been made.  For your current problem try this in terminal:

sudo update-grub

If windows still will not boot, I suggest marking this thread solved and opening a new one with a proper title.  You now need help with booting windows (I do not use windows) and a title saying so will better help you get the right help.

---

### Post by Jpendragon on 2012-09-26
All right, I tried it, it didn't work, I'll do a new thread, but before I do, can you tell me how to mark a thread as solved, I've been trying to figure it out for a while now....

---

### Post by jerrrys on 2012-09-26
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=mark+thread+solved&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=mark+thread+solved&as_qdr=all&sa=Google+Search&lang=en)

good luck :)

---

### Post by JKyleOKC on 2012-09-26
At the top of the page you'll find a toolbar with one entry titled "Thread tools." Select it, and there's one action to mark the thread as solved. Or follow the link in my sig to this message.

Have you read the messages from me on that "linuxbsdos" thread? It sounds as if you're caught in the UEFI vs Legacy bootloader conflict. You can install Boot-Repair into the Live-USB session and fix it, if that's the case...

And I just saw, a few minutes ago, that there's a new version of EasyBCD available that now plays nice with UEFI systems -- which it didn't, before. Haven't tried to test it, though, since my own problem system is now working nicely thanks to Boot-Repair.

---

