---
title: "Unetbootin MBR issue"
date: 2011-02-27
forum: General Help
---

### Post by DC Slick on 2011-02-27
Ok hi all, wasn't exactly sure where to post this but here goes: I have a dell mini 2133 2gb ram 320 gb hdd netbook that I have kubuntu 10.10 installed on one of 3 partitions (logical. Primary is a shared fat32 formatted partition so I can easily share files with winblows other is a swap). I had everything working all well and great until i attempted to make a bootable windows 7 flash drive using unetbootin. It over wrote the bootloader on my hdd. So, now when I boot my netbook I get the unetbootin default loop. I've been trying for two days to fix this. I have another laptop that I'm able to download tools to. A little help please...The other laptop is an XP box. I don't have an external optical drive otherwise i'd have just burned a disc and restored grub that way. I'm frustrated and can't think straight. Thanks in advance

---

### Post by seawolf167 on 2011-02-27
Can you boot from your UNetbootin or a live cd? Or burn a cd or create a new UNetbootin image on your other computer?

Once you get the live cd started, [here]("http://ubuntuforums.org/showthread.php?t=1195275") is a guide to reinstalling GRUB2 (see the section "Reinstalling GRUB 2 from LiveCD")

If you need Windows recovery disks (for things like fixboot, etc.), you can get them [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/").

---

### Post by DC Slick on 2011-02-27
No...netbootin didn't properly create the usb key either so it's unbootable (doesn't show a menu, doesn't show up on unetbootin menu) and the hdd is stuck in its default loop. I burned the live natty narwhal cd going to try that now...

---

### Post by seawolf167 on 2011-02-27
Once you get the Live CD, reinstall GRUB according to my previous links and you should be good to go. When you are then able to boot into Ubuntu, if you run 

```
sudo update-grub
```

in a terminal it should find your Windows install and make that bootable.

---

