---
title: "ubuntu and win xp"
date: 2009-12-12
forum: General Help
---

### Post by polardude1983 on 2009-12-12
Ok so I had ubuntu already installled, but wanted to install windows because of star wars galaxies and soon the new SWTOR. So i installed win xp and then it no longer gave me a option to boot my ubuntu anymore. it just went straight into windows. Well i took the ubuntu 9.10 live cd and reinstalled the grub to the mbr. And now it gives me an option of loading my ubuntu again at boot up but no windows now lol.

I was then reading this article [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

and it said to run this command in the terminal [COLOR=#ff0000][B]sudo gedit /boot/grub/menu.lst

[/B][/COLOR]and it says scroll down the bottom of the file but there is nothing in that file its completely blank. what do i do?

---

### Post by ST3ALTHPSYCH0 on 2009-12-12
Ubuntu 9.10 uses grub 2, the instructions you found are for grub legacy.
I think that if you run the update-grub command it will look for OSes again, but I won't swear to that, I'm still using grub legacy.

---

### Post by Iowan on 2009-12-12
[Here]("http://ubuntuforums.org/showthread.php?t=1195275") is a thread that may be helpful.

---

