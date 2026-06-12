---
title: "newbie question on dual boot screen"
date: 2006-03-14
forum: General Help
---

### Post by adityasn on 2006-03-14
I have installed red hat linux some time before and it comes with a GRUB loader. The same is with ubuntu, but when i loaded it with my XP system still in there I could not figure out the same screen as it was there with Red hat. I was thinking that the GRUB loader is the same for everything. Can anybody tell how to get that kinda screen in ubuntu? is it really possible or is it only for Red Hat?

This GRUB screen is very confusing. Secondly there is no way to change the default boot to Windows rather than linux. Please help???

---

### Post by TLE on 2006-03-14
First of all, the GRUB screen shouldn't be confusing. It should contain something like 4 lines you can choose between. One for Windoze and 3 for Ubuntu, a standard boot entry, a failsafe mode and a memory test. If you see something VERY different from that then there is probably something wrong.
Secondly, it is possible to configure the GRUB in Ubuntu to use Windoze as the default. The configuration file for GRUB is /boot/grub/menu.lst you need to edit this file to configure GRUB. First make a backup of it
```
cd ~/
cp /boot/grub/menu.lst .
```
Then edit it with gedit
```
sudo gedit /boot/grub/menu.lst
```
In this file are first some general settings, move down until you find the boot entries. They are section of code like this:
```

# For booting Windows NT or Windows95
title Windows NT / Windows 95 boot menu
root        (hd0,0)
makeactive
chainloader +1
```
or this
```
# For booting GNU/Linux
title  GNU/Linux
kernel (hd1,0)/vmlinuz root=/dev/hdb1
```
THE ONLY thing you need to do is to move the Wondoze boot section up so that it is the first one. Don't change anything else.
Once your done save it and reboot. If you broke the configuration file so that GRUB will not load, you can always boot from a rescue cd and copy the original menu.lst back. But let us hope that we will not have to go into that. Also check out [this link]("http://www.gnu.org/software/grub/manual/grub.html#Configuration") to read a little more on GRUB config.
Regards TLE

---

### Post by adityasn on 2006-03-14
thanks for the help. I was actually confused seeing those 3 different entries for ubuntu. Now its clear.

---

### Post by TLE on 2006-03-19
Actually it turnes out there is an even easier way to change the default boot entry, have a look at [this]("https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS"). I found it in another thread

---

