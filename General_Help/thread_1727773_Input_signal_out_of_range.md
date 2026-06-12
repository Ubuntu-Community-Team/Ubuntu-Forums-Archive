---
title: "Input signal out of range"
date: 2011-04-12
forum: General Help
---

### Post by ki4jgt on 2011-04-12
NOTE: I have to use noapic nolapic and acpi=off before my system will even boot. . . So I've chrooted the system and updated grub with these settings. Basically everything I've had to do, has had to be done from a liveCD and I would prefer if this was too.

As soon as my computer is turned on (After bios) Ubuntu makes the monitor display "Input signal out of range" It reccomends a 60Hz frequency and a display setting (Away from the computer)

Where do I go on the hard drive to edit these settings and do I have to chroot the system to update them?

---

### Post by 3rdalbum on 2011-04-12
Try removing the file /etc/X11/xorg.conf on the hard disk. If it doesn't exist, then you should do the following from the live CD:

Press Control-Alt-F1 to switch to a text terminal. Type:

```
sudo service gdm stop
sudo X -configure
sudo service gdm start
```

Now copy the "xorg.conf" file from the live CD's home directory, to the location /etc/X11/xorg.conf on the hard disk.

---

### Post by ki4jgt on 2011-04-13
Thanks

---

