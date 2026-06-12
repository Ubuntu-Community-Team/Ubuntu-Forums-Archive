---
title: "Laptop suddenly gets fatal error; boot not possible"
date: 2012-04-06
forum: General Help
---

### Post by Lukan27 on 2012-04-06
I was on my laptop chatting on Skype, making an update and played some music in the meantime. I went out to make a cup of coffee, and when I cam back music had stopped and the screen was all black with an underscore in the top-left corner. I did a hard reset, and suddenly GRUB showed up and gave me it's choices. Selecting the default boot it failed to load, and just stood there with white text. I could type, but nothing gave even a hint of response. Did a hard reset again, booted in GRUB with repair-option and tried to fix for disk errors, which it failed and prompted to do it manually, giving me the ability to write again, but with no responses. Hard reset again, and it now stalls at loading screen saying "Errors were found while checking the disk drive for /" and gives me some options, eg. F for attempt to fix errors. I press F to all my abilities, but nothing happens besides ffffffff etc. shows up to the right of the loading animation ("Ubuntu" with four dots). Other options gives same result.

Re-install is an option, but I seriously need some of the data on the disk.

And.. What on earth happened?


Specifications:

Lenovo ThinkPad Edge 11
Ubuntu 11.10

---

### Post by TeoBigusGeekus on 2012-04-06
Sounds like a hardware failure to me; my guess is the the hd is starting to fail.
Boot with a live cd/usb, backup your data and attempt an fsck to all your partitions:
```
sudo fsck /dev/sda1
```
etc.

---

