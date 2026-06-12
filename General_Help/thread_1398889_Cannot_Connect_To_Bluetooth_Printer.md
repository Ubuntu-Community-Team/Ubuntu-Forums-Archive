---
title: "Cannot Connect To Bluetooth Printer"
date: 2010-02-05
forum: General Help
---

### Post by robertneville777 on 2010-02-05
Hey guys whatsup!

Okay, I've run into a slight problem. As you can tell, I cannot connect to my HP printer through bluetooth. I've followed the Ubuntu documentation:

[https://help.ubuntu.com/community/BluetoothPrinterSetup]("https://help.ubuntu.com/community/BluetoothPrinterSetup")

but I get stuck at actually connecting to the device. Here's the terminal output:


robertneville777@robertneville777:~$ hcitool scan
Scanning ...
	00:17:D5:06:3D:8C	SAMSUNG SGH-T509
	00:1A:0E:C3:F7:29	Photosmart C5500 series
robertneville777@robertneville777:~$ hidd --connect 00:1A:0E:C3:F7:29
Can't open input device: No such file or directory (2)
robertneville777@robertneville777:~$

The "Samsung" is a cell phone, so we're not worried about that. My printer is an HP Photosmart C5580, so "00:1A:0E:C3:F7:29" is what we need to connect to.

Here's a pic of the terminal output on my desktop just for kicks, hehehe

[[IMG]http://i359.photobucket.com/albums/oo33/robertneville777/th_bluetooth_problem.jpg[/IMG]](http://s359.photobucket.com/albums/oo33/robertneville777/?action=view&current=bluetooth_problem.jpg)

Also, here's my printer specs:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01468798&lc=en&dlc=en&cc=us&lang=en&product=3575276]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01468798&lc=en&dlc=en&cc=us&lang=en&product=3575276")

Ubuntu is able to see it; it just can't connect for some reason. Anybody know how to fix this problem? I really want to use my printer ;) 

Thanks!

---

### Post by robertneville777 on 2010-02-05
C'mon guys... Not to be pushy, but I really need this printer working for school ;)

---

### Post by robertneville777 on 2010-02-05
Wow, guys, thanks for all your help...(I'm being sarcastic obviously)

Well anyway, I found the solution! You can find it here:

[http://www.linuxquestions.org/questions/fedora-35/bluetooth-printer-success-howto-611173/#post3854021](http://www.linuxquestions.org/questions/fedora-35/bluetooth-printer-success-howto-611173/#post3854021)

Yeah, the instructions are for Fedora, but they work perfectly fine for Ubuntu. 

I now have a bluetooth connected HP Photosmart C5580 printer! Ye!:guitar:

---

