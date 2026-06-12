---
title: "Ubuntu 11.04 Bluetooth Problem"
date: 2011-06-11
forum: General Help
---

### Post by renzobuntu on 2011-06-11
Hello All,

An Ubuntu Novice Here. :D

Just got my new laptop and decided to use Ubuntu 11.04 as my OS platform.

My Laptop is Acer 4750G 
Intel Core i5 
Nvidia GeForce GT 540M.

Had problems with the 3D Acceleration but luckily it was resolved already by downgrading to Unity 2D. ;)

And now experiencing problem with my Bluetooth. :(

In Bluetooth Preferences it shows that "Your computer does not have any Bluetooth adapter plug in" (But my laptop is integrated with Bluetooth 3.0).

And in Bluetooth Manager connection to BlueZ failed: Bluez daemon is not running, blueman-manager cannot continue.

I really want to enable my Bluetooth. :-|

Please help me with this issue.

Thank you and have a good one. :p

---

### Post by mkwa on 2011-06-20
I also have problem with bluetooth. I have two notebooks with small USB bluetooth adapters. When I power up, usually the bluetooth adapter is not enabled (does not blink blue). 

The fix for me is to reboot, and then bluetooth works.
Another fix is to restart bluetoothd deamon:

sudo killall bluetoothd
sudo /usr/sbin/bluetoothd --udev

With previous Ubuntu 10.10 I did not have this problem, the adapter always blinks blue after power up.

---

### Post by rgkb on 2011-06-21
have you turn on your bluetooth using fn + f3? mine is working

---

### Post by nipunshakya on 2011-09-06
First off all, check to see if your bluetooth is turned on or not buy switching the Wiress switch ON.....secondly, i would like to advice you to see the following link regarding bluetooth and its fixtures
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

I would also like you to install "Additional Drivers" software from Ubuntu Software Centre, (if it isn't preinstalled)..then, run the program to let it search hardwares available on your laptop...you probably might get some softwares missing on your laptop...let it download available drivers for u....best of luck...:)

---

