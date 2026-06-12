---
title: "Offline computer"
date: 2009-08-29
forum: General Help
---

### Post by Monotoko on 2009-08-29
Hiya

My friend had a computer that was running Windows which just would not boot any longer, so we tried to install Windows again and couldnt find the drivers.

So i suggested Ubuntu, and we got it installed successfully.

Now, i am faced with a problem:
She uses Vodafone Mobile Broadband, it requires some dongle thing which Ubuntu just will not recognise.

Now she says it is okay being offline because she has other computers, but is there any way i can at least get it to play MP3 files etc, because atm it just keeps asking to download the codecs.

---

### Post by LMZKJ on 2009-08-29
One simple way would be to download the files on one of the other computers that she has that is online and use a flash drive to bring them to the ubuntu machine.  Also, you might look to see if you can find a little more specific information on the dongle and ask if anyone else has had to deal with it.  I would bet there is a way to have Ubuntu pick it up.

---

### Post by Monotoko on 2009-08-29
Il have a look into that...

Do you know how she (or i..since she is still getting to grips with ubuntu) can get the packages?

All she really needs is the codecs

---

### Post by mac9416 on 2009-08-30
Hey, Monotoko, you can use [Keryx]("http://keryxproject.org/") to download ubuntu-restricted-extras so you can play MP3s.

---

### Post by dv3500ea on 2009-09-05
:D
Thanks for mentioning Keryx, it is an excellent piece of software. I installed Ubuntu yesterday and now I can install all the software I want without having to mess around with eciadsl drivers. Ubuntu works excellently, but it did seem to need an internet connection. This solves the problem of installing software. However, there is still the problem the drivers for my Nvidia Geforce 9300M GS graphics card aren't installed. If I had an internet connection they would install automatically. Is there a way to install them offline? I downloaded a .run file driver from the Nvidia website. It doesn't work though (it says that I need to run it as root) and it doesn't work with sudo from the terminal. Can anyone help?

---

### Post by EXCiD3 on 2009-09-05
dv3500ea, you need to hit Ctrl-Alt-F1 and install it from there with the following procedure:

<code>cd [directory where .run is located]
sudo /etc/init.d/gdm stop
chmod +x [.run file name]
sudo ./[.run file name]
sudo /etc/init.d/gdm start
</code>

Just replace the proper [] sections with what you need and you should be good to go. Glad to hear Keryx works well for you. :D

---

### Post by P4man on 2009-09-05
id still try to get that dongle working :)

Do you know what type it is? If you dont, plug it in, and run lsusb.

---

### Post by dv3500ea on 2009-09-06
:) Thank you, that worked.
Here's how I enabled visual effects:
```
sudo nvidia-xconfig --add-argb-glx-visuals
```

---

