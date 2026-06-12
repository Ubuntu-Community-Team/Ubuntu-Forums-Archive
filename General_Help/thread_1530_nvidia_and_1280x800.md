---
title: "nvidia and 1280x800"
date: 2004-10-21
forum: General Help
---

### Post by e.j. on 2004-10-21
just an fyi for anyone who might run into the same trouble as me. i have a widescreen 15.4" laptop running on nvidia, which runs best in 1280x800.

there are instructions elsewhere for getting the nvidia driver installed and running, but they left me in 1024x760. to change it, edit your /etc/X11/XF86Config-4`file and add the following line in the "Monitor" section:

ModeLine "1280x800" 80.58 1280 1344 1480 1680 800 801 804 827

i dont know that this is necessary, or even a good thing to do, but you also might want to switch your refresh rates in the same section to:

HorizSync 31.5-48.5
VertRefresh 40-70

save the file, then ctrl-alt-backspace to restart your x-server and you should be in lovely 1280x800.

e.j.

---

### Post by cybrjackle on 2004-10-21
Just a little warning, make sure your V&amp;H are the same as his :P  If your laptop is different, might not be a good thing.

---

### Post by Omegatron on 2006-10-15
> **e.j. said:**
> just an fyi for anyone who might run into the same trouble as me. i have a widescreen 15.4" laptop running on nvidia, which runs best in 1280x800.

I have the same problem with a 1680x1050.  Why isn't this an option in *System Settings --> Display*?

> to change it, edit your /etc/X11/XF86Config-4`file and add the following line in the "Monitor" section:

ModeLine "1280x800" 80.58 1280 1344 1480 1680 800 801 804 827
But what do all those numbers mean?  How would I set mine up for 1680x1050?

---

### Post by Gummi on 2007-02-12
Is this for Edgy? And how can I be sure if my "V&amp;H" are the same. I have an acer aspire 1690

---

### Post by vigleik on 2007-02-12
Isn't it safer (and easier) to do this with "sudo dpkg-reconfigure xserver-xorg"?

---

