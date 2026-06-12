---
title: "How to change keyboard layout?"
date: 2012-07-29
forum: General Help
---

### Post by daveman67 on 2012-07-29
I'm on ubuntu 12.04

Recently I bought a cheap apple style bluetooth keyboard. It pairs OK. I paired it with the current 102 key still attached.

Anyway I noticed that the character mapping is incorrect. Most keys do not type anything - some keys on the right (k, l, ;') etc give numbers, but that's about it.

So I rebooted, with 102 kbd unattached, and the bluetooth keyboard on, ready to connect.

After boot at the login screen, the bluetooth keyboard had paired. I typed my password, and it logged in fine!! However after the user login was complete it reverted to the broken behaviour. A glance at the layout chart shows ubuntu thinks I still have the 102 layout, even though it remained disconnected.

Any ideas?

Thanks, Dave

---

### Post by ragtag on 2012-07-29
Assuming it's a numbpadless keyboard, it just sounds like you have the function key toggled on. On most numbpadless keyboards you can use the right half as a numbpad when the function key is pressed or toggled on (j is 1, k is 2 etc). 

Look for a Fn key or similar on your keyboard, and press that, to see if it gets better.

---

### Post by daveman67 on 2012-07-29
Thanks a lot! I can now get the keyboard working kind of normally, but only if I toggle numlock with my 102kbd plugged in.

Also the function keys don't work yet - they're mapped to 'fn' functions, and 'fn' seems to have no effect in toggling them.

I'll keep trying.

Thanks, Dave

---

### Post by daveman67 on 2012-07-29
To fix the functions keys i just followed this

[https://help.ubuntu.com/community/AppleKeyboard#Change_Function_Key_behavior](https://help.ubuntu.com/community/AppleKeyboard#Change_Function_Key_behavior)


1. Append the configuration line to the file /etc/modprobe.d/hid_apple.conf creating it if necessary:

$ echo options hid_apple fnmode=2 | sudo tee -a /etc/modprobe.d/hid_apple.conf
2. Notify the hid_apple module to reload its configuration

$ sudo update-initramfs -u
3. Reboot

$ sudo reboot

---

