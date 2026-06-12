---
title: "number pad keeps moving the pointer"
date: 2009-08-10
forum: General Help
---

### Post by scarf on 2009-08-10
dear all,

i have ubuntu 8.10 installed and updated, and i am using a logitech MX 5500 keyboard/mouse with it.  this keyboard has a number pad which is a dedicated number pad.  there is no num lock key to transform the number pad to arrow keys/insert/delete/etc.

however, without notice, the number pad will stop working and will start controlling the mouse pointer.  what is it that causes this?

sometimes, it is simple to fix, by going to system > preferences > keyboard > mouse keys, and unchecking the box.

however, sometimes that doesn't work.  sometimes the box is already unchecked.

sometimes, i can hold down the shift key and use the number pad, and it will start producing numbers again.  after releasing the shift key, it continues to produce numbers and the issue is resolved.

sometimes, i have to unplug the bluetooth dongle from the back of the computer, plug it back in, and re-initiate the connection with the keyboard.

the only modification in the OS i have made regarding this keyboard, was to change HID2HCI_ENABLED=0 in /etc/default/bluetooth and /etc/init.d/bluetooth in order to make the keyboard work after the login screen loads.

---

