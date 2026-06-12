---
title: "Bluetooth mouse always double-clicks"
date: 2006-02-15
forum: General Help
---

### Post by jimisdead on 2006-02-15
I have had this problem for since I started using my bluetooth mouse and it is driving me insane.:( 

I am running Kubuntu 5.10 (and 6.04 with the same problem) on a Dell Inspiron 9300. Everything works perfectly, bluetooth adaptor is instantly recognised, I run 'sudo hidd --server' through a script at startup, and my mouse works straight away - but everytime I click it seems to register as a double click.

I have searched for many hours trying to find a solution, and have only come across one other instance of this sort of thing happening. But that was with a USB mouse and it was fixed by disabling the touchpad in xorg.conf, I tried that on my xorg.conf ([here]("http://www.spacemonkey.be/xorg.conf")) and restarted X but I still have the problem - (but I do suspect I may have done something wrong since my touchpad still works in KDE).

Does anyone have any idea?[-o<

---

### Post by raggamuffin on 2006-02-15
have you made sure in the Kcontrol center that the mouse is set to open files on a double click?....by default is set to open files on a single click...

---

### Post by jimisdead on 2006-02-16
[QUOTE=raggamuffin]have you made sure in the Kcontrol center that the mouse is set to open files on a double click?....by default is set to open files on a single click...[/QUOTE]

yes, I have my computer set to open files by double clicking.

I even wrote a small program so I could track what messages are being recieved from the input devices and every single click from the bluetooth mouse is registered as 2 button depressions then 2 button releases so I'm fairly sure it has something to do with xorg.

---

### Post by Paulo Wageck on 2006-02-16
you should turn off the regular mouse conector at your bios...
reinstall the system from scratch with the BT or USB wireless base on...
all should work fine....

worked for me... 

i use ubuntu/kubuntu with a microsoft wireless desktop 1000 as hardware

my board is an asus k8* series with and A64 3000

---

### Post by jimisdead on 2006-02-17
Thanks for the reply - I checked my bios but unfortunately it isn't able to disable the touchpad - I also looked into physically disconnecting the touchpad from the motherboard to no avail.

---

### Post by jimisdead on 2006-02-17
My apologies - after more investigation, coming to a total of 10 weeks, I have discovered the mouse is dodgy. Strangest thing is it works fine in Windows, but in Linux the left mouse button double clicks, so I switched to a lefthanded config and everything works fine as long as I don't need to right click too often.

---

### Post by Paulo Wageck on 2006-02-17
It took me a while to try that... now I am happy as hell.
The laser mouse will take a while to arrive... =)))

---

### Post by anath3ma on 2006-02-21
i have the exact same problem with a wireless targus mouse im using.  so, my question is...  is there any way to filter x-events?  that is, if two clicks come too fast then just send one click event?

---

