---
title: "usb external hdd not mounting."
date: 2011-02-24
forum: General Help
---

### Post by neba on 2011-02-24
Hello, I have an 3.5 sata hdd that I use as a external hdd. Everything has been working fine untill last week I pluged it in and nothing will show up I cant get the option to mount it. When I open gparted, the blue LED will blink a few times on the hdd. When I go to change devices in gparted all I get is /dev/sda. If I plug in an thumg drive then I will get the options of /dev/sda and /dev/sdc. So I think that it knows that /sdb is there, but I don't know why it wont pull it up...
any help would be nice. Thank you.

ps. my friends thinks it might be a logical error, I'm not sure what that means.

---

### Post by Foxheadz on 2011-02-24
Not sure if this will help much but whith it plugged in have you tried running ```
mount /dev/sdb
```

---

### Post by neba on 2011-02-25
Thank you for your reply. This is what I get
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab

Inside the case of the external hd it is conected by an IDE so i tried 
$ lsusb
Bus 002 Device 003: ID 14cd:6600 Super Top USB 2.0 IDE DEVICE
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

so I think it sees it there on the top one.

---

### Post by Foxheadz on 2011-02-25
ok so just edit /etc/fstab make a new line with something like

/dev/sdb/ /media/external *what ever format it is* 0 1

---

### Post by neba on 2011-02-25
Thank you, I have never edited fstab before. Do I place the new line at the botton? should it look like /dev/sdb/   /media/external    nfts

---

### Post by Foxheadz on 2011-02-25
/dev/sdb/ /media/external nfts 0 1 is what it should look like, also do you have the proper stuff to read ntfs drives?

---

### Post by neba on 2011-02-26
I don't think I do. On my other computer I have dual boot, the windows partition came right now with out me installing anthing. What should I install?

---

### Post by tredegar on 2011-02-26
Plug in your disk.

```
sudo fdisk -l
``` will tell you what disks / partitions linux can see.

Then you can decide how to mount them, and where.

If the above is confusing to you, please try that command, and post the output here, along with the output of the commands **mount** and **cat /etc/fstab**

---

