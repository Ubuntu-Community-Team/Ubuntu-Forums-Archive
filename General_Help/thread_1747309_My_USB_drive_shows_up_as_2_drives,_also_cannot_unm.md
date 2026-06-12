---
title: "My USB drive shows up as 2 drives, also cannot unmount or eject"
date: 2011-05-02
forum: General Help
---

### Post by Rytron on 2011-05-02
Hi.

My USB drive shows up as 2 drives and I also cannot unmount or eject. Because of this, I cannot use MultiSystem. :confused:

---

### Post by pricetech on 2011-05-02
What brand / model USB drive is it ??  Have you tried it on another computer ??

---

### Post by Rytron on 2011-05-02
> **pricetech said:**
> What brand / model USB drive is it ??  Have you tried it on another computer ??

Hi pricetech. It is a TrekStor and works fine on my Linux Mint 10 laptop. I have the same problem with other USB pen drives on my desktop Ubuntu 10.10 PC.

---

### Post by Rytron on 2011-05-03
I should also mention that I cannot add files to my USB drive! :confused:

This is a major inconvenience.

---

### Post by Rytron on 2011-05-04
I can copy files from the pen drive to my PC but cannot move files around on the pen drive (i.e. cut and paste). :confused:

---

### Post by fredrik-fyksen on 2011-05-04
Have you tried chown for getting acces to the memory pen?

In terminal:
"sudo chown YOURUSERNAME /media/NAMEONDRIVE"

---

### Post by Rytron on 2011-05-04
> **fredrik-fyksen said:**
> Have you tried chown for getting acces to the memory pen?

In terminal:
"sudo chown YOURUSERNAME /media/NAMEONDRIVE"

Thanks but no joy.

---

### Post by Morbius1 on 2011-05-04
There is only one thing I know of that mounts usb devices to usbx and that's usbmount. If you have it remove it:

```
sudo apt-get remove usbmount
```

---

### Post by Rytron on 2011-05-04
> **Morbius1 said:**
> There is only one thing I know of that mounts usb devices to usbx and that's usbmount. If you have it remove it:

```
sudo apt-get remove usbmount
```

Bingo! You got it Morbius1. Thank you very much.

---

### Post by jchw on 2011-05-14
I have exactly the same problem and I tried sudo apt-get remove usbmount. It seemed to work and I can now bring up the stick but I cannot use it to move files so my USB stick is useless at the moment.

I use a 32G USB stick for my backups so this is a serious issue. The problem seemed to stem from about a week ago and I wonder if it happened after a routine update? I see some other people seem to have the same problem but have put it down to the upgrade to 11.4. I am still on 10.10 so it cannot be 11.4 related.[IMG]file:///home/john/Desktop/Screenshot.png[/IMG]

---

### Post by jchw on 2011-05-14
Sorry should have added this screenshot.

---

### Post by Rytron on 2011-05-15
> **jchw said:**
> I have exactly the same problem and I tried sudo apt-get remove usbmount. It seemed to work and I can now bring up the stick but I cannot use it to move files so my USB stick is useless at the moment.

I use a 32G USB stick for my backups so this is a serious issue. The problem seemed to stem from about a week ago and I wonder if it happened after a routine update? I see some other people seem to have the same problem but have put it down to the upgrade to 11.4. I am still on 10.10 so it cannot be 11.4 related.[IMG]file:///home/john/Desktop/Screenshot.png[/IMG]

Have you tested the USB Pen Drive on another PC to make sure it is not the problem? Also try the advice from **fredrik-fyksen** in a post above and do this in a terminal:
```
sudo chown YOURUSERNAME /media/NAMEONDRIVE
```

---

