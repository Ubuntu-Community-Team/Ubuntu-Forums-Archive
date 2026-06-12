---
title: "no fn-key == no webcam - plz help"
date: 2011-01-16
forum: General Help
---

### Post by johnnyslogan on 2011-01-16
Hi all,

I use Ubuntu 10.10 on a Medion PC (E6220), and everything is fine and dandy ... except, the webcam does not work. Well actually I think it does work, and I also think, that Ubuntu would recognize it, if it was turned on. The problem however is, that in order to turn it on, I need to press fn+F9, and that key combo simply does not work ... neither does the fn+F7 combo, which toggles the wifi - but that is less important, since wifi is on and works. 

Logging into i.e. win7, toggling the webcam there, and then back into Ubuntu is not really an option at the moment. So right now I seem to be stuck in a situation, where a non-defined keyboard shortcut equals no webcam at all. The obvious question of course is: Is there a way to force the webcam on without the key-combo?

Any help would be much appreciated.

Best regards,
Jakob

---

### Post by tredegar on 2011-01-16
Nobody has replied, so ......

What is the webcam? (the output of **lsusb** should tell you )

As for turning it on, sometimes just running **cheese** is enough to do this (it is for both my PCs with built-in webcams (Asus EEE and Sony Vaio))

Otherwise there might be something relevant in **/proc/acpi/*** (hint - have a good look through all those subdirectories. 

**/proc** is a virtual filesystem that gives you a view of, and lets you alter, the kernel's view of all sorts of things. Eg I have the "file" **/proc/acpi/video/NGFX/LCD/brightness** and **sudo echo 4 > /proc/acpi/video/NGFX/LCD/brightness** changes the brightness of my screen.

---

### Post by no2498 on 2011-01-16
try the fn+f4 just to see if the light turns on

sudo apt get install cheese

to try the cam with

---

### Post by johnnyslogan on 2011-01-17
Hi,

Thank you very much for your replies! I tried the lsusb output earlier, but no webcam seems to be on the list, but here it is anyway:

```
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Apart from that, I've been in Cheese (and guvcview) with no success. 

And thank you for the proc-acpi-tip, but alas, I cannot locate anything resembling a webcam. Anything in particular, I should be searching for?

As for the fn+F4 combo, it turns off my screen, which I think it is supposed to do, but it doesn't turn on my webcam. 

I really think the webcam should work, partly from reading this gentleman's post:

[http://ubuntuforums.org/showthread.php?t=1570039](http://ubuntuforums.org/showthread.php?t=1570039)

And as earlier stated, booting into Windows 7(/Vista/XP etc.) is not really an option at the moment.

Regards

---

### Post by tredegar on 2011-01-17
> I really think the webcam should work, partly from reading this gentleman's post:
If there is nothing useful in your BIOS, it looks like you are stuck. So you can either just wait (maybe forever) or perhaps it's time to buy a USB camera. [This site]("http://www.ideasonboard.org/uvc/") should be helpful.

---

### Post by no2498 on 2011-01-17
he turned the cam on in windows frist

I used Windows to switch on the Webcam. The Bios is set to remember the last state. So now I can use the Webcam in Ubuntu.

---

### Post by no2498 on 2011-01-17
he turned the cam on in windows frist

I used Windows to switch on the Webcam. The Bios is set to remember the last state. So now I can use the Webcam in Ubuntu.

---

### Post by johnnyslogan on 2011-01-17
Hi,

Well, I do have the disabled and remember last state options, but not the - at the moment much needed - 'turn on and stay on in OS'-option.

Regards, and thank you again for your answers.

---

