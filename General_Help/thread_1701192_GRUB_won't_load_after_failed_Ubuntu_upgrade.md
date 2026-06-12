---
title: "GRUB won't load after failed Ubuntu upgrade"
date: 2011-03-06
forum: General Help
---

### Post by Quazze on 2011-03-06
Hello

[B]When I start my computer GRUB starts, but it only says:

Grub Loading stage1.5.
Grub loading, please wait...

and nothing happens[/B]

Here is what happened before:
I had a dual boot on my computer with Windows and Ubuntu. There was also a problem with Windows, but that's another thing. Now I had not upgraded Ubuntu for a long time. I think I still had Ubuntu 8.9 . So I wanted to upgrade and let Ubuntu do it automatically, it showed the upgrade to 9.4. So let it upgrade, but it asked if it had to change menu.lst, but since I had menu.lst modified in the right way, I choose the option to keep the already installed version. But it just kept asking the same question, so 4 or 5 times and a few hours later I choose the option to change it to the default package version. Then it didn't ask this anymore, but it hung at a later stage. So I waited several hours longer, but it didn't proceed anymore, so I had to shut it down. It shut down OK, but then when I restarted, what I described above happened.

Now I have another problem, **my disk reader (CD/DVD) doesn't work either**, so I cannot simply use a LiveCD...

So can anyone help me with this? Can I boot from a USB-stick? And how do I fix this?

Many thanks in advance, and sorry if this is already posted, but I didn't find it.

---

### Post by runeh76 on 2011-03-06
WoW! U dont like to update ur system?  :)

I think its better use ur LiveCD and take backups. Then DL example 10.04 or 10.10 and make a new install.


edit: Oh u sayed u cant use ur CD.. Do u have bootable distro in USB?

---

### Post by Quazze on 2011-03-06
well, it is not that I don't like to upgrade, but I just forgot about it because I didn't very often used Ubuntu since I couldn't get my sleepfunction to work

I don't have a bootable distro in USB, but can I do it like this:
[https://help.ubuntu.com/community/Installation/FromUSBStick#live-usb](https://help.ubuntu.com/community/Installation/FromUSBStick#live-usb) ?

Don't I have to configure my computer to boot from USB? Can I do that if nothing loads?

(thanks for the quick reply!)

---

### Post by runeh76 on 2011-03-06
Yeah exactly! 
U need to download "some_distro".ISO though 
read part: (Creating a bootable Ubuntu USB flash drive)

Good Luck!

---

### Post by Quazze on 2011-03-06
thanks, i'll try that

---

### Post by runeh76 on 2011-03-06
np, im here if u need help later..

---

### Post by Quazze on 2011-03-06
ah, yes, just one question
so I have made the bootable USB drive, but so when I use it to boot Ubuntu from "LiveUSB" is it possible (i.e. will also not give problems) to mount my other partitions (for making back ups) like the Windosw partition (so NTFS)? And if I have to force the mount (since there might have been an unclean shut down by windows)?

---

### Post by Quazze on 2011-03-06
ai, I don't seem to be able to get into my BIOS
GRUB immediately starts loading, but doesn't continue...

---

### Post by drs305 on 2011-03-06
Quazze,

Do you know why you can't get into your BIOS? Do you know the correct key to press as the system powers up? If not, you can do a search of your BIOS or computer brand to learn the correct BIOS-entry key to press.

Once you are able to boot to any Ubuntu desktop or terminal, you should be able to mount your real Ubuntu installation. Assuming it installed correctly, you could then reinstall Grub2. I would recommend completely removing it and then reinstalling (as long as you have an Internet connection). Here is a guide on how to do that. It say's LiveCD but USB will also work as long as you can get it to boot.
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by runeh76 on 2011-03-06
Everything is possible, u can example use Gparted to make a new partition and backup stuff there.

When u reboot ur computer, u should see some text on the screen to access BIOS. Try F1  ESC  DEL

---

### Post by Quazze on 2011-03-06
ok sorry, my bad. I can get in my BIOS, I used the wrong key (and since it doens't say on the screen which button to use, I thought that still had to come)

And I can indeed get to my original Ubuntu installation. It's no problem though (now I have back-ups of my most important files) to reinstall Ubuntu. If I install Ubuntu 10.10, will it then automatically reinstall GRUB (and thus GRUB 2) or will I still have to that?

---

### Post by eghonam on 2011-03-06
when i use update manger to update the security bakege he say no net i use ubunto10.10 and i have net so what's the problem

---

### Post by drs305 on 2011-03-06
> **Quazze said:**
> And I can indeed get to my original Ubuntu installation. It's no problem though (now I have back-ups of my most important files) to reinstall Ubuntu. If I install Ubuntu 10.10, will it then automatically reinstall GRUB (and thus GRUB 2) or will I still have to that?

If you still have pieces of Grub legacy and do an upgrade it may still ask if you want to keep the old Grub. My advice would be to just make a backup copy of /boot/grub/menu.lst and let it overwrite Grub with Grub2. If it doesn't ask, it probably means that it didn't find any old Grub legacy files and will just install the latest version of Grub (probably 1.98 in your case).

---

### Post by runeh76 on 2011-03-06
> **eghonam said:**
> when i use update manger to update the security bakege he say no net i use ubunto10.10 and i have net so what's the problem

Post terminal errors output: ```
sudo apt-get update
```

---

### Post by Quazze on 2011-03-06
ok, thank you both very much. Everything seems to be ok now (although it gave some errors when shutting down from liveUSB after installing Ubuntu and when booting, but it works fine)

much appreciated

---

