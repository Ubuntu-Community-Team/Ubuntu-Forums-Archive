---
title: "I don't even know how to search for this problem"
date: 2009-11-18
forum: General Help
---

### Post by Phyxiis on 2009-11-18
I am dual booting Ubuntu 9.10 and XP Pro. When the GRUB comes up and gives me options to pick (Ubuntu or XP Pro) there is a list. At first there were like a few choices 

-Ubuntu 9.10 (regular ubuntu)
-Ubuntu 9.10 (recovery mode)
-+memtest86 (not sure if that is exact)
-XP Pro


NOW however, there are 4 seperate Ubuntu startups and the memtest and XP Pro

-Ubuntu 9.10 (regular ubuntu)
-Ubuntu 9.10 (recovery mode)
-Ubuntu 9.10 (regular ubuntu)
-Ubuntu 9.10 (recovery mode)

They have different numbers so I'm assuming that they are UPDATES or something.

My question is how do I get it down to just UBUNTU 9.10 (regular and recovery mode), MEMTEST, XP PRO?

---

### Post by ubername on 2009-11-18
There are a nunber of ways.

Grub looks to see what OS's are installed and gives you options for each. With Linux distro's it gives two options, a normal one and a 'recovery one.

Options to change your menu are (depends whether you are using legacy grub or grub2 as to how to do these: search these forums for howto's)
1. edit the grub file /boot/grub/menu.lst or /boot/grub/grub.cfg 
2. change the grub options as to how many 'old versions' of ubuntu are displayed 
3. uninstall old ubuntu kernels (but you should always keep at least one 'old' for safety's sake)

---

### Post by Giblet5 on 2009-11-18
Boot into Ubuntu (the first one listed).

Open a terminal (Applications -> Accessories -> Terminal)

Enter the following command: ```
sudo dpkg -l | grep linux-image
```

Those are all of the linux kernels you have installed via updates. Scary, huh!

Remove all of them except the two highest-numbered ones.

It will look something like: ```
sudo apt-get remove linux-image-2.6.31-12-generic linux-image-2.6.31-11-generic linux-image-2.6.31-10-generic --purge
```

Now, they're gone, so let's update the grub menu. Use copy and Shift+Ins to enter these commands in the terminal, one at a time:

```
sudo update-grub
sudo grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```

Now, when you boot, it will only have the two most recent kernels.


Bonus: you have a bit more free disk space now.

---

