---
title: "not able to access cell phone contents"
date: 2009-09-05
forum: General Help
---

### Post by agrawal on 2009-09-05
When I connect my nokia mobile phone to my laptop via a data cable, I am able to see the "USB drive" icon in my file browser but when i try to open, it displays the error message as
"Unable to mount location

No media in the drive"

Can anyone help me out?!!!!!!!!

---

### Post by Liolikas on 2009-09-05
Looks like Ubuntu thinks that you have external card reader not phone. Try to insert card into phone.

---

### Post by agrawal on 2009-09-05
> **Liolikas said:**
> Looks like Ubuntu thinks that you have external card reader not phone. Try to insert card into phone.
i have 1GB memory card inserted in my phone

---

### Post by Roasted on 2009-09-05
When I plug in my razr, it reads it as external media since I have a micro sd card in the phone.

It does the exact same thing in windows xp.

---

### Post by Liolikas on 2009-09-05
Personally I use USB bluetooth to connect to my phone.Even better no need for wires you can just keep phone in pocket.

---

### Post by agrawal on 2009-09-05
is thr any way of accessing my memory card which i hav inserted in my cell phone?

---

### Post by agrawal on 2009-09-05
ya thts good... hey can u tell me the procedure to activate bluetooth in my laptop... I am not much familiar using ubuntu...

---

### Post by Grenage on 2009-09-05
Normally when you plug in the phone, the phone will give you the option of connecting as a mass storage device, or via the nokia suite etc.  Naturally pick the mass storage option.

---

### Post by agrawal on 2009-09-05
> **Grenage said:**
> Normally when you plug in the phone, the phone will give you the option of connecting as a mass storage device, or via the nokia suite etc.  Naturally pick the mass storage option.
Only after selecting that option, I am facing that problem. Nokia PC suite anyways does not run in Ubuntu..rite?

---

### Post by agrawal on 2009-09-05
> **Grenage said:**
> Normally when you plug in the phone, the phone will give you the option of connecting as a mass storage device, or via the nokia suite etc.  Naturally pick the mass storage option.
Only after selecting that 'mass storage' option, I am facing that problem. Nokia PC suite anyways does not run in Ubuntu..rite?

---

### Post by Liolikas on 2009-09-05
> **agrawal said:**
> ya thts good... hey can u tell me the procedure to activate bluetooth in my laptop... I am not much familiar using ubuntu...

Just buy USB device they are cheap connect and that is all I think for Ubuntu. Icon will appear. Example adapter:
[http://www.dlink.com/products/?pid=34](http://www.dlink.com/products/?pid=34)

---

### Post by Liolikas on 2009-09-05
[http://www.smokinglinux.com/tutorials/nokia-pc-suite-for-linux-with-obextool-on-ubuntu-gutsy](http://www.smokinglinux.com/tutorials/nokia-pc-suite-for-linux-with-obextool-on-ubuntu-gutsy)

---

### Post by agrawal on 2009-09-05
> **Liolikas said:**
> Just buy USB device they are cheap connect and that is all I think for Ubuntu. Icon will appear. Example adapter:
[http://www.dlink.com/products/?pid=34](http://www.dlink.com/products/?pid=34)
i already hav bluetooth in my laptop but i dont know how to activate it

---

### Post by Liolikas on 2009-09-05
Strange why it do not work...you for sure do not have icon or sth?
Try then:
sudo /etc/init.d/bluetooth start

---

### Post by Roasted on 2009-09-06
System - Preferences - Bluetooth "Icon Always On"

Icon appears in upper right corner. Right click it. Set up new device.

---

### Post by justborn on 2009-09-06
dude i think using it via bluetooth would be easier.if ur phone's bluetooth is switched on the comp will recognize it automatically.i dont suppose u have to install a bluetooth driver,or configure,or install an bluetooth software(is installed by default).

after the u pair ur device ,right click and use the '**browse device**' option.and rest is just click and drag,all made easy.

---

