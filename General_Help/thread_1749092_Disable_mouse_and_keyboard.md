---
title: "Disable mouse and keyboard"
date: 2011-05-04
forum: General Help
---

### Post by thexnightmare on 2011-05-04
Dear,
How can I permanently disable mouse and keyboard usage?
So if user plug in a mouse or keyboardm they will not work?
Thx

---

### Post by thexnightmare on 2011-05-07
where are you experts?

---

### Post by matt_symes on 2011-05-07
Hi

Can i ask why you want to disable the keyboard and mouse ? How do you intend to administer the computer ?

Kind regards

---

### Post by thexnightmare on 2011-05-08
We develped special hardware which we want to  demoonstrate in a kiosk.
the user will u a touch screen. and we want to prevent  him from connecting a mouse and keayboard to not play with anything.

---

### Post by matt_symes on 2011-05-08
Hi

Have a read of this. I would try to disable the connectors from the motherboard as one of the poster suggested.

[http://superuser.com/questions/273639/disable-usb-keyboards-mice-etc-in-ubuntu-10-10](http://superuser.com/questions/273639/disable-usb-keyboards-mice-etc-in-ubuntu-10-10)

Kind regards

---

### Post by thexnightmare on 2011-05-08
no, I am searching for software solution, however thx for ur suggestion.

---

### Post by matt_symes on 2011-05-08
Hi

Have you thought about unloading the keyboard and mouse drivers or disabling them though X ? That might work.

something along the lines of

```
sudo modprobe -r <driver_name>
```

or using

```
xinput set-prop
```

I have to be honest. These are suggestions and not solutions as i have never needed to do what you are asking. Still, i am trying to help you.

Kind regards

---

### Post by thexnightmare on 2011-05-10
but what is the drivername parameter for the keyboard and mouse?

---

### Post by matt_symes on 2011-05-11
Hi

Is there an option to disable keyboard and mouse input in the BIOS on the target machine ? What is the make and model of the target machine ?

What type of keyboard and mouse are you trying to disable. Are they USB keyboards and mice ? If you have no other USB devices you might be able to disable the USB subsystem in the BIOS.

You might also be able to disable the USB subsystem from grub. Try passing ```
nousb
``` as an option to the kernel from grub.

Also, have a read of this. It uses xinput set-prop to disable keyboard and mouse input. It may work for you if you are running X. Give it a try.

[http://wpkg.org/Disable_/_enable_keyboard_and_mouse_in_Linux](http://wpkg.org/Disable_/_enable_keyboard_and_mouse_in_Linux)

What version of Ubuntu are you planning on disabling the keyboard and mouse for ?

Kind regards

---

### Post by thexnightmare on 2011-05-11
Thx alot,
No the option is not found on BIOS.
I am using Karmic 9.1, and xinput works great, the alot sir.

---

