---
title: "Safely Uninstalling Ubuntu"
date: 2006-06-17
forum: General Help
---

### Post by just2good4u3434 on 2006-06-17
I installed Ubuntu about 2 months ago and couldnt be happier, but the problem is my sister and I both use the same computer and she doesnt like to use Ubuntu because shes really stupid. Anyway since I wasnt using Ubuntu and i needed the hard drive space I decided to uninstall Ubuntu. I used Partition Magic to format the partition that Ubuntu was on, and then i moved that space to another partition. I had to restart for the changes to take effect, so I restarted. I wasnt able to get anywhere after the restart. It said something like...

Loading Grub..
Error loading Grub
error 15

and thats it nothing else happened. I figured the boot loader got deleted. So i panicked a little. I decided i needed to get the boot loader back. So I spent some time reinstalling Ubuntu. Everything went fine and Grub was reinstalled. It told me to take out the linux and restart. I restarted and Grub loaded and I loaded Windows XP. I logged on to my user name and a window popped up saying that new hardware or software was installed and I had to restart for the hardware or software to work. I went to restart later and i found that nothing was loading and my system wouldnt start up. But i went to CTR ATL Delete and restarted from there. I restarted and a Grub failed to load again. Im REALLY screwed if i cant get this fixed by tonight. I cant reformat my windows partition cause i have some very important data on it. I have a windows XP cd and an Ubuntu cd. PLEASE HELP!!

---

### Post by xXx 0wn3d xXx on 2006-06-17
Follow [ this tutorial to re-install grub. ](http://doc.gwos.org/index.php/Restore_Grub) You will not need to re-install ubuntu or xp, this tutorial requires a ubuntu install disc.

---

### Post by codejunkie on 2006-06-17
[quote=just2good4u3434]I installed Ubuntu about 2 months ago and couldnt be happier, but the problem is my sister and I both use the same computer and she doesnt like to use Ubuntu because shes really stupid. Anyway since I wasnt using Ubuntu and i needed the hard drive space I decided to uninstall Ubuntu. I used Partition Magic to format the partition that Ubuntu was on, and then i moved that space to another partition. I had to restart for the changes to take effect, so I restarted. I wasnt able to get anywhere after the restart. It said something like...

Loading Grub..
Error loading Grub
error 15

and thats it nothing else happened. I figured the boot loader got deleted. So i panicked a little. I decided i needed to get the boot loader back. So I spent some time reinstalling Ubuntu. Everything went fine and Grub was reinstalled. It told me to take out the linux and restart. I restarted and Grub loaded and I loaded Windows XP. I logged on to my user name and a window popped up saying that new hardware or software was installed and I had to restart for the hardware or software to work. I went to restart later and i found that nothing was loading and my system wouldnt start up. But i went to CTR ATL Delete and restarted from there. I restarted and a Grub failed to load again. Im REALLY screwed if i cant get this fixed by tonight. I cant reformat my windows partition cause i have some very important data on it. I have a windows XP cd and an Ubuntu cd. PLEASE HELP!![/quote] 
With your windows xp cd in the drive, boot it up like your going to reinstall windows. It should give you the option of entering the recovery console, choose the recovery console option, when you get to the command prompt, enter ```
fixboot
```press enter, when that finishes enter ```
fixmbr
```now enter```
exit
```to reboot your computer this will restore the windows bootloader. now you can use partition magic to remove the ubuntu partition and recover the drive space.

---

