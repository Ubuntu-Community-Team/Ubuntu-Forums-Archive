---
title: "Brand new reinstall. No usplash"
date: 2009-10-08
forum: General Help
---

### Post by SpitfireSMS on 2009-10-08
Just reinstalled literally 2 hours ago.
I was getting all my drivers and apps installed, and I decided to go with a new usplash.
After downloading startup manager, usplash isnt showing at all.

Heres my menu.lst:
```
title		Ubuntu
uuid		6a90d38c-6201-473d-8baa-d8b1aca4e208
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6a90d38c-6201-473d-8baa-d8b1aca4e208 ro quiet splash vga=0x0318 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet
```

I see the splash, but its not happening.
Any ideas?

---

### Post by Brandon Williams on 2009-10-11
Run update-usplash-theme to find out what themes the system thinks are available. For example:
```
$ update-usplash-theme
Installed themes:
usplash-theme-ubuntu
usplash-theme-xubuntu
```

Select one of the themes, and then run update-usplash-theme with the theme name as an argument:
```
$ sudo update-usplash-theme usplash-theme-xubuntu
Using '/usr/lib/usplash/usplash-theme-xubuntu.so' to provide 'usplash-artwork.so'.
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
```

If the theme you want isn't listed, then you'll need to do the things that update-usplash-theme does for you.
```
$ sudo ln -s /path/to/theme.so /etc/alternatives/usplash-artwork.so
$ sudo update-initramfs -u
```

---

