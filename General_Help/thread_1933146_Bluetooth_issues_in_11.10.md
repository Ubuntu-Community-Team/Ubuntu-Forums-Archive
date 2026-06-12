---
title: "Bluetooth issues in 11.10"
date: 2012-02-28
forum: General Help
---

### Post by fruscian on 2012-02-28
I'm having an issue with the Bluetooth in Ubuntu 11.10
So, I have an external wireless speaker by Creative that I like to use, and it works fine; I added the device and can connect to it with the built in Bluetooth icon on the desktop no problem.
However, I've noticed that periodically, usually after my computer comes out of 'suspend' mode, the bluetooth stops working and when I click on the icon, it says the bluetooth is on, but the menu does not come up. (With the list of devices, and the option to connect, etc...)
I've tried turning it off and on, but that doesn't work. To use the bluetooth when this happens, I have to restart the computer. Once it restarts, it works fine again. But it's a bit annoying, having to restart the computer so often just to use the bluetooth.

Any ideas how to fix this?
Also, I'm very much a novice Linux user. this is my first time using this operating system. Bear with me. :)

Thanks

---

### Post by fragos on 2012-02-29
When my bluetooth acts up I open a terminal window and run:

    sudo service bluetooth restart

I then check the bluetooth icon because sometimes I have to do this twice to get it working.

---

