---
title: "Ubuntu graphics problem."
date: 2012-07-25
forum: General Help
---

### Post by Zestypanda on 2012-07-25
Just wanting to say that my install of elementary os luna (built on top of a fresh install of ubuntu 12.04lts) has a bug with my graphics card, and might be solely related to ubuntu, my graphics card is an asus (ati sub brand) 6670 HD 1gb card, and if I don't edit grub and add "nomodeset" when it boots the login screen is messed up and the desktop wont even load, yet if I set it to "nomodeset" it will load but is extreamly laggy, but last time I tried to install the ati drivers to get 3d acceleration to work (assuming without them they are running on software render) it crashes and dumps me at a ttyl prompt, so without the drivers and "nomodeset" enabled in grub elementary desktop, unity 2D, and unity 3D are extremely laggy, and the computer has 4gb ram 2.5ghz core 2 duo extreme so I don't know if this is solely an ati driver/ubuntu issue, or it's something with elementary also, and when I try to send a bug report the bug report program reports it cannot send logs.

---

### Post by ranger1021994 on 2012-07-25
Its a driver issue.
You can manually install ati drivers by downloading .run files from their site
OR
reinstall fglrx from synaptic

---

### Post by Zestypanda on 2012-07-25
but it crashes and dumps me at a ttyl prompt when I install the driver from the ati site, and if I install the fglrx driver it says that there was a failure installing

---

### Post by QIII on 2012-07-25
Sometimes the installation fails using the "Additional Drivers" method or synaptic.

If you still have the driver from the AMD website installed, 

```
sudo aticonfig --uninstall
```

Reboot.

Then, see the ATI driver wiki in my signature.  In the table of contents, click the section that starts with "Using the Ubuntu repositories (alternate command line method ..."

---

### Post by ranger1021994 on 2012-07-25
You can try this :

[http://askubuntu.com/questions/98827/ati-driver-re-install-fail](http://askubuntu.com/questions/98827/ati-driver-re-install-fail)

---

### Post by QIII on 2012-07-25
That is an older version of the driver.  The instructions for installing 12.6 manually are in the wiki I directed the OP to if he wants to do it that way. 

Even though the repo contains version 12.4, i recommend using the repo because manual installation requires reinstallation if the kernel is updated during normal updates.  The repo method does not.

---

### Post by Zestypanda on 2012-07-30
I tried the instructions on the wiki with a clean install of ubuntu and still nothing, I have posted a new thread with a question I just thought of.

---

### Post by Zestypanda on 2012-12-18
Ok, I was able to get it to work, I just downloaded the .sh file, selected "run as executable" and then clicked it, then clicked "open in terminal" and I'm all set. ^_^ Thanks guys.

---

