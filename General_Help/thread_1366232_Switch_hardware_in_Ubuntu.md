---
title: "Switch hardware in Ubuntu?"
date: 2009-12-28
forum: General Help
---

### Post by RobLikesBrunch on 2009-12-28
My PCI WiFi card doesn't play very nice with Ubuntu, and I have a USB network card lying around that I'd like to use instead. Ubuntu recognizes the card when I use lsusb and I know the card is supported. However, I have no idea how to instruct Ubuntu to stop using the PCI card and instead use the USB card.

So if anyone could instruct me how to make the switch, that'd be great.

---

### Post by warfacegod on 2009-12-28
Take the card out?

---

### Post by RobLikesBrunch on 2009-12-28
> **warfacegod said:**
> Take the card out?

Obviously that's a solution, but 1) I'm too lazy and 2) I'm curious to see how I would go about selecting hardware in Ubuntu without a GUI-based device manager.

---

### Post by 3rdalbum on 2009-12-28
Assuming the PCI card is wlan0:

```
sudo ifconfig wlan0 down
```

If you want this to happen every time on boot, add the following to /etc/rc.local (before the "exit 1" line):

```
ifconfig wlan0 down
```

the contents of rc.local run as root anyway so you don't need sudo.

---

### Post by RobLikesBrunch on 2009-12-28
> **3rdalbum said:**
> Assuming the PCI card is wlan0:

```
sudo ifconfig wlan0 down
```If you want this to happen every time on boot, add the following to /etc/rc.local (before the "exit 1" line):

```
ifconfig wlan0 down
```the contents of rc.local run as root anyway so you don't need sudo.

Brilliant! Thanks!

Edit: rc.local ends with end 0, not end 1 for me....should I change it?

---

### Post by falconindy on 2009-12-28
> **RobLikesBrunch said:**
> Brilliant! Thanks!

Edit: rc.local ends with end 0, not end 1 for me....should I change it?

Absolutely not.

exit 0 = exit with success
exit 1 = exit with error

I'm sure the above poster was merely making a reference to the location in the file and wasn't paying attention to clerical accuracy.

---

