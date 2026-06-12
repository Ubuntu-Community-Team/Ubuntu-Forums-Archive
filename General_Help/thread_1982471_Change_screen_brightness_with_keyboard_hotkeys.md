---
title: "Change screen brightness with keyboard hotkeys"
date: 2012-05-18
forum: General Help
---

### Post by fizikz on 2012-05-18
I have been unable to change the screen brightness using my laptop's hotkeys (Fn +F4/F5) since Ubuntu 11.04. I have now upgraded to 12.04 and the problem persists. Other hotkeys such as those for volume, wifi, and suspend all work fine, just not for the brightness. I'm using an Asus G1. I've noticed others have this problem as well with other brands of laptops too. Has anyone solved this?

---

### Post by MiXor on 2012-05-18
Hi!
I've had this issue on my laptop too. It is a mac, and the fix is given in [https://help.ubuntu.com/community/MacBookPro7-1/Oneiric#Keyboard_functions_.28Brightness.2Cvolume.2C....29](https://help.ubuntu.com/community/MacBookPro7-1/Oneiric#Keyboard_functions_.28Brightness.2Cvolume.2C....29)
The asus G1 has an NVIDIA card too, so it might work for you...
Best of luck!

Aline

---

### Post by fizikz on 2012-05-18
Thanks for the link. I tried it, but it didn't work for me.

---

### Post by MiXor on 2012-05-19
Sorry... :(
I found this (for precise): [http://manpages.ubuntu.com/manpages/precise/man1/alt-nvidia-current-xconfig.1.html](http://manpages.ubuntu.com/manpages/precise/man1/alt-nvidia-current-xconfig.1.html)

Good luck!

---

### Post by fizikz on 2012-05-19
Are you refering to the following option?

>        --enable-acpi-hotkeys, --no-enable-acpi-hotkeys
              The "EnableACPIHotkeys" option can be specified to override  the
              NVIDIA  X  driver's  default  decision to enable or disable ACPI
              display change hotkey events.

I checked my xorg.conf, and it is already enabled. Funny thing is that the backlight on/off hotkey works. It's just the brightness adjustment that does not.

---

### Post by fizikz on 2012-07-02
Has anyone found a solution to this? In addition to the above, I have tried editing /etc/default/grub to include "acpi_osi=Linux, acpi_backlight=vendor" on the line for GRUB_CMDLINE_LINUX_DEFAULT. Still does not work.

I noticed that when setting gnome keyboard shortcuts, the Fn+F5/F6 (brightness up/down) keys are not recognized as a key combo. I wonder if this could be a clue. 

On the other hand, ```
cat /sys/class/backlight/acpi_video0/brightness
``` works to query the current brightness, and ```
cat /sys/class/backlight/acpi_video0/max_brightness
``` gives a numerical value for the max brightness, which is 15 in my case. Then, the brightness can be changed with a command like: ```
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

(Taken from a post [here]("http://askubuntu.com/questions/57236/unable-to-change-brightness-in-a-lenovo-laptop").)

Perhaps a script could be written for use with xbindkeys.

So, the software works for changing brightness, but the keyboard hotkeys don't work, and are not recognized in gnome keyboard shortcuts. Any suggestions would be really appreciated!

---

### Post by fizikz on 2012-09-07
Finally, my brightness hotkeys work. I found the solution here: [http://askubuntu.com/questions/168197/brightness-controls-stopped-working-after-update-on-a-samsung-qx412-s01au]("http://askubuntu.com/questions/168197/brightness-controls-stopped-working-after-update-on-a-samsung-qx412-s01au")

Basically, in /etc/default/grub, change the line with GRUB_CMDLINE_LINUX_DEFAULT to include "acpi_osi=" and do 'sudo update-grub'

---

