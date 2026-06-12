---
title: "Grub2 took over Grub Legacy"
date: 2010-07-17
forum: General Help
---

### Post by Axolotl9250 on 2010-07-17
Hi, I had Arch Linux installed on my machine on sda1 and the Grub legacy that came on their install image on the MBA at sda/. I just did a Ubuntu update and it wanted me to do an update and me thinking grub-install referred to grub legacy, went along with it but now I have Grub2 for my boot menu. There are a few guides on restoring Grub2 I've found but how do I put Grub back on to how I had it? (I thought installing grub legacy from Arch's usb image I have would be simple and fairly automated/easy but it won't let me without doing the previous steps of partitioning drives and selecting packages to install and such so it looks like I'm going to have to do it manually which I haven't done before).

---

### Post by Bachstelze on 2010-07-17
Boot a Live CD, mount root partition where your menu.lst is installed, and

```
sudo grub-install --root-directory=/mnt/foo /dev/sda
```

Obviously, said Live CD must have GRUB Legacy (though why you still want to use it is beyond me...).

---

### Post by oldfred on 2010-07-17
If you have grub2, I do not recommend going back to grub legacy. Grub2 is a lot better at finding other systems. What changes do you want to make to the menu.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)


HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

---

### Post by Axolotl9250 on 2010-07-17
Ok well I'd like all the config stuff to be on my Arch partition as currently I believe it has all grub stuff like menu.lst. But basically I'd like Arch to be the default and I' like it to only show one entry for Ubuntu, rather than several for different kernel versions.

[EDIT] I've read through editing GRUB2 and although it's slightly more complex and not KISS I think I do still like it. I've not been meddling with GRUB and GRUB2 for long, up till now I've let it all do whatever it wants. If I did the install command on another partition with a distro on it for grub 2, then I'm guessing that would screw things up because of more than one set of configuration files and such yes? Because I've been mulling this over because when I installed Ubuntu I deliberately didn't install a bootloader because I already had grub legacy. But when I ran updates it wanted to install grub2 anyway, which basically put it in control of booting i.e. I have to come into Ubuntu and edit the files to alter the boot-menu - I couldn't do it in Arch or something else I may happen to be using. Luckily Arch hasn't reacted to having grub2 but Ubuntu was damned adamant it wanted it when I updated so would other distro's I may come to use - or Ubuntu, play up and rebel and maybe not work If I gave control to another partition / another distro?

For Now I will probably leave it as is.

---

