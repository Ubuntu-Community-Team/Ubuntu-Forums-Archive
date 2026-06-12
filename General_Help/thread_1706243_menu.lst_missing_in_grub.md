---
title: "menu.lst missing in grub"
date: 2011-03-13
forum: General Help
---

### Post by rajnikhil on 2011-03-13
Hi All,

I want to install slackware (i.e. dual boot) along with ubuntu 10.04. I've read some threads as to how to do this and came to know that we need to skip installation of LILO in slackware installation and an entry for slackware in the menu.lst file of grub. I thought I'll take a look at the file before I actually start the installation however I didn't find this file at all in the grub directory.

Can someone please tell me if it is normal for this file to be missing or is something wrong here? if there is something wrong then what do I do?

Also can you tell me how to find the UUID?

Thanks in advance for the help.

---

### Post by wilee-nilee on 2011-03-13
> **rajnikhil said:**
> Hi All,

I want to install slackware (i.e. dual boot) along with ubuntu 10.04. I've read some threads as to how to do this and came to know that we need to skip installation of LILO in slackware installation and an entry for slackware in the menu.lst file of grub. I thought I'll take a look at the file before I actually start the installation however I didn't find this file at all in the grub directory.

Can someone please tell me if it is normal for this file to be missing or is something wrong here? if there is something wrong then what do I do?

Also can you tell me how to find the UUID?

Thanks in advance for the help.

You have grub2, there is no menu.list run this command to confirm the grub loaded.
```
sudo grub-install -v
```
it will show something like this probably.
grub-install (GRUB) 1.98+20100804-5ubuntu3.1
Grub legacy which your looking for would show .97

The good thing is that grub2 will automatically read the lilo and put it its bootmenu, I did this like 5 days ago with slackware myself.

But after installing slackware you need to reload grub to the mbr.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Some suggest as you have described, but I have found with both lilo and grub-legacy which is where the menu.list would be are picked up with no problem, and just reloading the grub2 to the mbr works fine.

---

### Post by ajgreeny on 2011-03-13
I have no knowledge of slackware so don't know about its installation, but if you can do so, install the new OS with no grub or lilo at all.

After you've installed it, reboot into ubuntu, run ```
sudo update-grub
``` and slackware should appear in ubuntu's grub menu.

---

### Post by andrew.46 on 2011-03-17
> **rajnikhil said:**
> Also can you tell me how to find the UUID?

UUID can be found with blkid. An example on my slackware system:

```

root@skamandros/home/andrew# blkid
/dev/sda1: UUID="02a99ba2-9208-465c-8a3d-3d88bae2da73" TYPE="ext4" 
/dev/sda2: UUID="07030c77-332c-49f7-944e-0af9f17d3fda" TYPE="swap" 
root@skamandros/home/andrew# 

```

There is a plethora of options that can be used with the blkid command but the bare command might be enough.

---

