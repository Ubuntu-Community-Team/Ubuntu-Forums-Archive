---
title: "Black screen tryong to boot from live cd/usb"
date: 2011-11-05
forum: General Help
---

### Post by alx_gom on 2011-11-05
I just got a Gateway NV55S09U(AMD A6 3400m), and i`m trying to intall oneric 64bit on it, but when i boot from the usb or the live cd i get a black screen.

Any ideas how to fix it?

---

### Post by dcstar on 2011-11-05
> **alx_gom said:**
> I just got a Gateway NV55S09U(AMD A6 3400m), and i`m trying to intall oneric 64bit on it, but when i boot from the usb or the live cd i get a black screen.

Any ideas how to fix it?

Sometimes it can get hung on certain hardware, press CRTL-C or CTRL-ALT-DEL and see if it then progresses.

---

### Post by alx_gom on 2011-11-07
> **dcstar said:**
> Sometimes it can get hung on certain hardware, press CRTL-C or CTRL-ALT-DEL and see if it then progresses.


Doesn't work :s . What acually happens is that when the ubuntu 11.10 screen with the dots appears, the monitor shuts down.
I've tried connecting an external monitor to the laptop but i had he same problem.

---

### Post by bbrg548 on 2011-11-07
> **alx_gom said:**
> Doesn't work :s . What acually happens is that when the ubuntu 11.10 screen with the dots appears, the monitor shuts down.
I've tried connecting an external monitor to the laptop but i had he same problem.

With the AMD A6 3400m processor, you can't install 11.10 directly due to an issue with the 3.0.x kernel trying to use the fglrx graphics drivers even if they aren't actually installed. You have to start by installing 11.04, install the fglrx package, then upgrade to 11.10.

---

### Post by alx_gom on 2011-11-07
> **bbrg548 said:**
> With the AMD A6 3400m processor, you can't install 11.10 directly due to an issue with the 3.0.x kernel trying to use the fglrx graphics drivers even if they aren't actually installed. You have to start by installing 11.04, install the fglrx package, then upgrade to 11.10.


ok, it worked until the fglrx driver. I've installed natty, now when i want to download the drivers packages from synaptic i get this error:
" E: No se pudo bloquear /var/cache/apt/archives/lock - open (11: Recurso no disponible temporalmente)
E: No se ha podido bloquear el directorio de descargas "

translation: E: couldn't block  /var/cache/apt/archives/lock - open(11: resourse not available  termporarily)
E: couldn't block download directory.

when i try to install it from aditional controlers it frezes after it starts downloading.

---

### Post by mikeroberts on 2011-11-27
I feel your pain. It took me around 8 hours to get Ubuntu installed on this machine. Fooled around with xorg config settings and lots of different things but it is actually a quick and simple process when you have all the steps figured out and will take about 45 minutes to an hour if you follow my instructions :).

This is installing directly from 11.10 cd (usb didn't work out for me). I've done this on two of these machines and both are working perfectly.

1. This is going to sound weird, but keep restarting and booting from cd until you get to the install ubuntu screen, i don't know why this happens, but I got a black screen the first few times and after 4 or 5 boots it gets to the installer screen. 

2. Press f6 and select nomodeset and then hit escape and press enter on install ubuntu. Let ubuntu do its thing and install, should install fine.

3. On reboot hold shift to bring up grub and boot into recovery mode. When the options screen for recovery mode select resume normal boot and it will boot into command line.

4. Login with your credentials and sudo apt-get install fglrx and whatever else you want to install right now to make setup a little faster. I use mine for web dev so I installed lamp-server^ and a few other things.

5. sudo reboot

It should now work properly and that should've taken you all of an hour.

p.s. DO NOT UPDATE YOUR KERNEL TO 3.1! I tried this and it worked fine for a day or two. Kernel 3.1 has a bunch of updates to how it manages power and processing and this laptop flied after installing that! It was noticeably much faster, possibly even 2x as fast. But I installed some updates and then it wouldn't boot. Had to boot into old kernel version and purge 3.1 kernel. I would suggest waiting until it comes through the update pipeline.

---

### Post by alx_gom on 2011-11-27
> **mikeroberts said:**
> I feel your pain. It took me around 8 hours to get Ubuntu installed on this machine. Fooled around with xorg config settings and lots of different things but it is actually a quick and simple process when you have all the steps figured out and will take about 45 minutes to an hour if you follow my instructions :).

This is installing directly from 11.10 cd (usb didn't work out for me). I've done this on two of these machines and both are working perfectly.

1. This is going to sound weird, but keep restarting and booting from cd until you get to the install ubuntu screen, i don't know why this happens, but I got a black screen the first few times and after 4 or 5 boots it gets to the installer screen. 

2. Press f6 and select nomodeset and then hit escape and press enter on install ubuntu. Let ubuntu do its thing and install, should install fine.

3. On reboot hold shift to bring up grub and boot into recovery mode. When the options screen for recovery mode select resume normal boot and it will boot into command line.

4. Login with your credentials and sudo apt-get install fglrx and whatever else you want to install right now to make setup a little faster. I use mine for web dev so I installed lamp-server^ and a few other things.

5. sudo reboot

It should now work properly and that should've taken you all of an hour.

p.s. DO NOT UPDATE YOUR KERNEL TO 3.1! I tried this and it worked fine for a day or two. Kernel 3.1 has a bunch of updates to how it manages power and processing and this laptop flied after installing that! It was noticeably much faster, possibly even 2x as fast. But I installed some updates and then it wouldn't boot. Had to boot into old kernel version and purge 3.1 kernel. I would suggest waiting until it comes through the update pipeline.




Sorry, i forgot to update, it worked installing the 11.04, then the amd drivers and then 11.10.

Though i still can't use gnome 3, unity sometimes works wrong and the screen when i turn off the computer doen's appear how it should. But for now i use xfce until some updates fix the problems unity still has.

---

### Post by mikeroberts on 2011-11-27
> **alx_gom said:**
> Sorry, i forgot to update, it worked installing the 11.04, then the amd drivers and then 11.10.

Though i still can't use gnome 3, unity sometimes works wrong and the screen when i turn off the computer doen's appear how it should. But for now i use xfce until some updates fix the problems unity still has.

Weird...Unity and gnome3 work perfect for me

---

### Post by timozattol on 2011-12-04
hey guys, I just saw this Thread, maybe you can help me I have almost the same problem and I didn't really undestand the Solution of yours =)

Thanks a lot 

[http://ubuntuforums.org/showthread.php?p=11512012#post11512012](http://ubuntuforums.org/showthread.php?p=11512012#post11512012)

---

