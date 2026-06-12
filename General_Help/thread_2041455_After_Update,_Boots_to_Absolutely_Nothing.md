---
title: "After Update, Boots to Absolutely Nothing"
date: 2012-08-12
forum: General Help
---

### Post by khoraski on 2012-08-12
I know I recently posted a question for help, but that was because I was having trouble using Ubuntu again after such while. 

And now while using Ubuntu again (10.04 LTS), it asked me if I wanted to install updates. I said sure, and then it asked me if I wanted to reboot my computer. 

I also said yes, but when my computer rebooted, it just boots to a black screen with the flashing underscore cursor. There's absolutely no output and it does not let me input anything. 

When I recently asked for help, someone linked me to a boot-repair app that worked. I tried that this time, and it did not work. [Here]("http://paste.ubuntu.com/1143508/") is what it linked me to after the boot repair was finished, if that is helpful at all.

Here is just a pic of GParted, don't know if you need it, but you mostly request it when I ask for help with something:

[IMG]http://i.imgur.com/9nsri.png[/IMG]

I also have Windows 8 CP installed at sda3.

Like I said, it just boots to absolutely nothing. There's the flashing cursor, but it does not allow me to type anything nor does it write anything for me to read.

---

### Post by drs305 on 2012-08-12
Is the Boot Info script link recent (made after your updates and attempted repair)? The results indicate that BR was able to fix your system by reinstalling Grub to sda.

Are you sure your system is booting first from your Ubuntu drive (try removing any other external device)?

Also, regarding the blinking cursor. Two things could cause this: the system is finding no Grub/bootloader or it's booting to your Ubuntu OS but you have lost your video drivers. To see if it's the second case, try holding down the SHIFT key during boot and see if the Grub menu appears. 

If it does, edit the menuentry by pressing 'e' and adding *nomodeset* to the 'linux' line. Remove *quiet splash* as well, then F10 or CTRL-x to boot.

---

### Post by khoraski on 2012-08-12
> **drs305 said:**
> Is the Boot Info script link recent (made after your updates and attempted repair)? The results indicate that BR was able to fix your system by reinstalling Grub to sda.

Are you sure your system is booting first from your Ubuntu drive (try removing any other external device)?

Also, regarding the blinking cursor. Two things could cause this: the system is finding no Grub/bootloader or it's booting to your Ubuntu OS but you have lost your video drivers. To see if it's the second case, try holding down the SHIFT key during boot and see if the Grub menu appears. 

If it does, edit the menuentry by pressing 'e' and adding *nomodeset* to the 'linux' line. Remove *quiet splash* as well, then F10 or CTRL-x to boot.

I was able to get it working again using these steps, thanks.

---

