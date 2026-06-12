---
title: "Wireless USB key not working"
date: 2009-10-22
forum: General Help
---

### Post by sigixv on 2009-10-22
Hi all,

I bought a wireless network usb key today but i cant get it to work

The key is a[ Hercules HWNU-300]("http://www.hercules.com/us/wifi/bdd/p/72/hercules-wireless-n-usb-key-hwnu-300-/")

My current system is karmic amd64 with 2.6.31-14-generic kernel, fully updated. No other Wifi is present in the system

I followed [this tutorial]("http://www.generation-linux.fr/index.php?post/2008/12/24/Clef-USB-Wifi-Hercules-HWNU-300") via a link on the french ubuntu forum but no joy.
He tested ndiswrapper and others without result and based his howto after contacting the manufacturer Hercules on the [Ralink RT2870USB chipset]("http://www.ralinktech.com/support.php?s=2") with either the [2.2.0.0 patch]("http://www.generation-linux.fr/public/mai09/hwnu300.patch") or the experimental [2.6.31]("http://www.generation-linux.fr/public/sept09/hwnu300-2.6.31.patch") with the following code:
```
cd *RT2870_Linux_STA*
patch -p0 < hwnu300.patch
sudo make && sudo make install
sudo modprobe rt2870sta
```and then to configure manually the device in
/etc/Wireless/RT2870STA/RT2870STA.dat

I tried both patches without result, the procedure as he mentions goes without trouble, except for the fact that the folder /etc/Wireless/ doesnt exist/ isnt created.
In the replies at the bottom there is talk that as from kernel 2.6.27 the chipset was integrated already...

So it looks like i'm not the only one having trouble getting this device up & running. Almost all info is in french (making it somewhat harder to read for me :)), but also there isn't a fullproof how to just yet so it seems.

Any ideas here on the main forum?

---

### Post by sigixv on 2009-10-23
bump

---

### Post by sigixv on 2009-10-24
nobody?

---

### Post by enzipher on 2009-12-04
Hi sigixv,

For a long time I have been trying to get my Hercules HWGUSB2-54-V2 to work with Ubuntu but I never succeeded, up until now after finding your post. :)

I can't know if it works with your dongle, but here is what I did on Ubuntu 9.10 (I used a live CD but it shouldn't matter).

First I followed "Seconde procédure" in the tutorial you specified, which is for Ubuntu 9.10, to install the driver.

Second I edited the RT2870STA.dat

[FONT="Courier New"]$ sudo gedit /etc/Wireless/RT2870STA/RT2870STA.dat[/FONT]

...and changed these lines:

[FONT="Courier New"]SSID=MySSID
AuthMode=WPAPSK
EncrypType=AES[/FONT]

If you have other settings for you connection you should make changes to reflect those.

After that it just worked, and months of frustration is finally over. :)

Hope it works for you as well.

Good luck!

---

### Post by sigixv on 2009-12-04
Thanks! Finally a reply :)

I'll give it a go later this weekend and hopefully it will work.

---

### Post by enzipher on 2009-12-06
Happy if I can help, let me know how it goes.

---

### Post by sigixv on 2009-12-06
Didn't have the time to switch to the computer with the wireless key this weekend. I'll get back to this next week and post the results.

---

### Post by sigixv on 2009-12-23
Sorry i wasnt able to reply any sooner, but i've got it working in the end. Both in linux box as in XP: same machine, different HD (not a dual boot).
I do however not recommend anyone in buying this device. It constantly disconnects: every few hours (or sometimes even minutes) when it fails to maintain the Wifi connection and has to reconnect. As a result downloads, IM conversations and online gaming are unpleasant or even impossible...
*nix distros require manual fiddling to get it to work and for windows it will only operate on old drivers with XP, on win7 it'll do nothing at all and with updated drivers it even disables the landriver... :confused:

Anyways, i call this thread "solved" with a big questionmark for now but i believe the main problem lies here with the manufacturer.
As the box says: "Hercules Wireless Attitude: Puur Plezier ... Niet te moeilijk"[I]
(loosely translated from dutch: "Pure enjoyment ... Not too complicated")
[/I]I differ in my opinion somehow...

Once again thanks to enzipher for taking the trouble to write back on the forum.

If anyone were to find a fullproof method to get this bloody wifi usb key working without concurrent crashes, i would be happy to learn about it

sigixv

---

