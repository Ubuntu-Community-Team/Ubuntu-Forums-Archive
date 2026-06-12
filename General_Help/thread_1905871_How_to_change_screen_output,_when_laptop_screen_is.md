---
title: "How to change screen output, when laptop screen is broken?"
date: 2012-01-07
forum: General Help
---

### Post by yamaha10 on 2012-01-07
My laptop (Samsung N510) screen is broken and I've recently  tried to install ubuntu 11.10. I'm planning to use the laptop with HDMI  connected to my TV. While installing from a USB stick, both laptop screen (cracked with just  light on) and my TV is displaying. When installation is finished and it  reboots internal screen is the only one displaying. 
  Since I cannot see anything on that screen I was wondering if there  are some way to type some kind of a shortcut or how to get into the  settings without seeing anything. 
  
[LIST]
[*]I've tried the fn+F4 buttons that has the screen on it, but nothing happens.
[*]I've also tried plugging HDMI cable in before startup, nothing  happens, plugging the HDMI cable in while it's on does not work either.
[*]I've tried unplugging my laptop screen before startup, with HDMI plugged in, (worked in windows) but then the laptop won't boot.
[/LIST]
  Is it impossible?

---

### Post by bluexrider on 2012-01-07
**1)**
Open **sudo gedit /etc/default/grub**


**2)**
Change the line:
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**

to 

**GRUB_CMDLINE_LINUX_DEFAULT=""**

Save the changes and exit.

**3)**
Run this command to update the changes to Grub:
**sudo update-grub**

**4)**
Reboot

Hope this helps

---

### Post by yamaha10 on 2012-01-08
Thanks for the quick reply. But I can't see anything on the laptop screen other then that it's on. Is there any way I can do this without seeing anything and just use my keyboard?

---

