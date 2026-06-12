---
title: "Boot options Windows 7 and Ubuntu 10.10"
date: 2010-10-13
forum: General Help
---

### Post by bunnsnow on 2010-10-13
I am in a bit of a predicament and wondered if anybody could help.

I previously had Windows 7 and Ubuntu running together (dual boot) separating the HDD 50/50. When i booted up my machine I had 2 options on the boot menu. Windows 7 and Ubuntu respectively.

I recently re-formatted my HDD re-installing Win7 and Ubuntu 10.10. Now when I boot my computer I get 5 options.

[LIST=1]
[*]Linux pae
[*]Linux (recovery - i think)
[*]memory test
[*]win7
[*]win7 recovery
[/LIST]
I just wondered if I could change it back to the simple 2x options?

Thanks in advance

---

### Post by yetiman64 on 2010-10-13
Please have a good read of link #2 in my sig, particularly section 5 regarding grub2 files and options before using this below.

To turn off the memory test option,

```
sudo chmod -x /etc/grub.d/20_memtest86+
```The recovery console is very handy, particularly if you need to reset your password or fix the system when other problems stop you accessing your machine. However it is up to you if you want it shut off and it can be turned off with,
```
gksudo gedit /etc/default/grub
```then change the line
> #GRUB_DISABLE_LINUX_RECOVERY="true"**TO**
> GRUB_DISABLE_LINUX_RECOVERY="true" note only the # symbol is removed (ie the line is uncommented).

To ensure these changes are implemented by grub2 use in terminal,
```
sudo update-grub
```This should now leave your grub boot menu with three entries (if your original description of the menu is correct)

1 Linux pae
2 Win7
3 Win7 Recovery

I won't suggest touching your Windows entries at all myself, but others here may be able to help you some more if need be.

Also as new kernels are released the list will grow by 1 with each release. It is generally recommended to keep the latest **two** kernels at least (for booting and troubleshooting if your newest kernel fails for some reason - particularly important if you remove the linux recovery entry).

---

### Post by Quackers on 2010-10-13
Before amending the Windows entries I would suggest that you boot into Windows using them. This is because sometimes grub2 can label them the wrong way round (Recovery entry can actually boot up your live system and vice versa). You wouldn't want to delete the wrong one!

---

### Post by bunnsnow on 2010-10-13
Yetiman/Quakers. Thank you very much for your detailed replie, I could not have asked for better responses!
I'm fairly new to the Ubuntu forums but am very happy I signed up. I like helping others and being helped :-)
I will try your suggestions later this evening when I am at home - at work at the minute
THANKS AGAIN!

---

### Post by Quackers on 2010-10-13
I'm not a Quaker! I'm a duck! :-)
You're welcome - have fun :-)

---

