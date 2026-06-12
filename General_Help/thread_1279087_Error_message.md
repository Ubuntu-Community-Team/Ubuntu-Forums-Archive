---
title: "Error message"
date: 2009-09-30
forum: General Help
---

### Post by blertie2 on 2009-09-30
[FONT=Arial][SIZE=3]I was trying to add a repository link I had found to install Linbaku (back up utility).[/SIZE][/FONT][FONT=Arial][SIZE=3]
[/SIZE][/FONT][FONT=Arial][SIZE=3]
[/SIZE][/FONT][FONT=Arial][SIZE=3]Half way through it went wrong and gives me this Error message:[/SIZE][/FONT]

   [FONT=Comic Sans MS]Error: opening the cache (E: malformed line 54 in source list /etc/apt/sources.list (absolute dist), E: the list of sources could not be read.) This usually means that your installed packages have unmet dependencies[/FONT]


[FONT=Arial][SIZE=3]I have tried reading up on many Terminal commands to rectify it all to no avail. Nothing is available until I put in my password which it will not allow me to do.[/SIZE][/FONT]


[FONT=Arial][SIZE=3]Originally the ASUS had it's own Linux OS installed which I did not like so I managed to install Ubuntu from a pen drive, which went onto the 3.5GB partition, however this was too small to allow updates and installations so I then installed it to the 16GB partition and formatted the smaller space.[/SIZE][/FONT]
[FONT=Arial][SIZE=3]Now I get the offer of two OS at boot up, one of which is not really there, and although I have told it to look for Removeable media to boot up from first, it no longer recognises the pen drive until it has booted into the OS on the larger partition.[/SIZE][/FONT]


[FONT=Arial][SIZE=3]So you see, I cannot re-install Ubuntu either.[/SIZE][/FONT]


[FONT=Arial][SIZE=3]blertie2@hotmail.com
[/SIZE][/FONT]

---

### Post by Megrimn on 2009-09-30
create this entry in /boot/grub/menu.lst next to the other boot options


> **Megrimn said:**
> 

```

   title Run Ubuntu 9.04 from USB DISK
   root (hd0,0) 
   kernel      /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash ignore_uuid xforcevesa
   initrd      /casper/initrd.gz
```



then reboot and select this option.  It should boot from the usb drive.

---

### Post by blertie2 on 2009-09-30
Thanks Megrimn but it says permission denied

---

### Post by j.bell730 on 2009-09-30
You need sudo privileges:
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Megrimn on 2009-09-30
> **j.bell730 said:**
> You need sudo privileges:
```
sudo gedit /boot/grub/menu.lst
```

yeah, forgot about that.

---

