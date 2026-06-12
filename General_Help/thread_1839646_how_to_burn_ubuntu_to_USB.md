---
title: "how to burn ubuntu to USB"
date: 2011-09-06
forum: General Help
---

### Post by Gladiator-prog4me on 2011-09-06
Hi ,

please help me , how to burn ubuntu ISO to usb , and then boot it to install ? 

because i don't have a dvd room and want to install ubuntu 11.11 beta 1 

thank you

---

### Post by jg2345 on 2011-09-06
What operating system are you currently using?

---

### Post by axatrikx on 2011-09-06
see the ubuntu documentation on the topic 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Gladiator-prog4me on 2011-09-06
> **jg2345 said:**
> What operating system are you currently using?


ubuntu 11.04

---

### Post by Gladiator-prog4me on 2011-09-06
now i try : startup disk creator ..

---

### Post by jfed on 2011-09-06
For creating a LiveUSB I like to use unetbootin

```
sudo apt-get install unetbootin
```

It's very easy to use. You launch it, select the option to use an .iso, rather than the preset OS choices, and then just browse to the iso. Your USB drive should be selected by default. After that it'll extract and burn the files to the usb and you can then boot from it.

Hope this helped!

---

### Post by Gladiator-prog4me on 2011-09-06
now , i'am burn the iso to usb , and then change the bios boot to usb-hdd 

but when i restart the computer , it's not boot from usb !

please help me

---

### Post by axatrikx on 2011-09-06
hav u changed the primary boot device as usb in bios?
if not change it n try

---

### Post by Gladiator-prog4me on 2011-09-06
> **axatrikx said:**
> hav u changed the primary boot device as usb in bios?
if not change it n try

yes , the first boot is usb

---

### Post by axatrikx on 2011-09-06
try using usb-imagewriter
here is the link to the guide 
[http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html](http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html)

---

### Post by jfed on 2011-09-06
If you have the .iso burnt to the usb, and your primary boot option is the usb-hdd, then what exactly is the problem still? Does it not work?

If so, on startup go into the boot menu and manually choose usb-hdd.

---

### Post by Gladiator-prog4me on 2011-09-06
> **jfed said:**
> If you have the .iso burnt to the usb, and your primary boot option is the usb-hdd, then what exactly is the problem still? Does it not work?

If so, on startup go into the boot menu and manually choose usb-hdd.


yes this is the problem , so how to go into the boot menu ?

---

### Post by Gladiator-prog4me on 2011-09-06
F12 :)

i have go into boot menu and choose usb-hdd , but this not work again !! 

i have attached a screenshot from file into USB Flash memory .

---

### Post by jfed on 2011-09-06
So you went into the boot menu, and select the USB-HDD option, and it STILL doesn't boot from the LiveUSB? Well thats very odd, try putting it in a different usb port, or installing it to a different usb drive. Could you use a CD or DvD?

---

### Post by Gladiator-prog4me on 2011-09-06
> **jfed said:**
> So you went into the boot menu, and select the USB-HDD option, and it STILL doesn't boot from the LiveUSB? Well thats very odd, try putting it in a different usb port, or installing it to a different usb drive. Could you use a CD or DvD?

 i have a problem on my dvd room so i want to use usb , now i will try a different usb port and different usb drive and tell you the result , thank you for your help :)

---

### Post by nothingspecial on 2011-09-06
Use unetbootin instead. usb-creator-gtk is not working propperly for me either at the moment. unetbootin is.

---

### Post by Gladiator-prog4me on 2011-09-06
now it's working :) 

thank you every one .

---

