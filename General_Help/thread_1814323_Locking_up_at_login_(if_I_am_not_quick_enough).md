---
title: "Locking up at login (if I am not quick enough)"
date: 2011-07-29
forum: General Help
---

### Post by babakott on 2011-07-29
[SIZE=2][COLOR=Black]I recently purchased a [Toshiba Satellite C655D-S5202.]("http://www.meetgadget.com/gadget/50547/Toshiba+Satellite+C655D-S5202")[/COLOR][/SIZE]
[COLOR=Black][SIZE=2]
It runs an AMD Dual-Core C-50 APU @ 1ghz w/Radeon HD 6250 , 2gb ram (upgrading to 8gb), a Realtek RTL8188CE b/g/n wireless card. It's basically a next gen netbook with a 15.6 Truebrite display. (however for the price and hardware its a little beast)

Initially Xubuntu would hang on install (and later boot-up) unless I plugged the nic into the router, which hinted to me the problem might be the wireless card. So I downloaded the kernel module from Realtek, compiled and installed it into the Kernel and boom, everything was OK, except for one thing. 

When I boot, I literately have seconds to enter my password or the system will hang on the xfce login screen. [/SIZE][/COLOR][COLOR=Black][SIZE=2]It will also lock while booting, but it is very rare. [/SIZE][/COLOR][COLOR=Black][SIZE=2]Once I am logged in it works with zero issues.

I really don't know what to check for this kind of behavior, so any pointers would be great.

Thanks. 

------------------------------------
I thought I would post the fix for anyone else that may have the issue.

The fix was pretty simple. The NIC/Wireless, as it turns out is a combo card. If you unplug the cat 5 from the nic, Linux (not just Ubuntu) tries to switch over to wireless but gets confused. 

The fix is to setup the system using the nic with the alternate install CD, and right before the first boot, go into the bios and turn off "PCI Lan". Once you boot up, configure your wireless. 

If you need wired Ethernet at a later date, boot to the bios, turn on the PCI Lan, plug in the cable and then boot regularly into Ubuntu. The main issue here is you cannot have the PCI Lan on, and try to use the wireless.

Hope this is helpful somewhere down the road.
[/SIZE][/COLOR]

---

