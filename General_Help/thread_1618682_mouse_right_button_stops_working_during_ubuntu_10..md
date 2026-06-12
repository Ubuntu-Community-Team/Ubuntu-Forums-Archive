---
title: "mouse right button stops working during ubuntu 10.10"
date: 2010-11-10
forum: General Help
---

### Post by brettybaby on 2010-11-10
this happens to me every day

I'll be on ubuntu 10.10 and the right button the mouse stops working

I have to restart to get it to work again

does anyone know what this is? :confused:

---

### Post by bigpayne69 on 2010-11-10
I haven't heard of anyone else with this issue, have you checked to make sure that your mouse isn't the problem? What type of mouse are you using?

---

### Post by brettybaby on 2010-11-11
> **bigpayne69 said:**
> I haven't heard of anyone else with this issue, have you checked to make sure that your mouse isn't the problem? What type of mouse are you using?

its not the mouse; its the software; maybe a virus; I guess Ubuntu 10.10 is vulnerable

If I reboot the mouse works.  The touch pad and Usb mouse do the same thing at the same time unless rebooted.

this is a software problem

---

### Post by Ancanus on 2010-11-11
It used to happen to me as well.

You might want to do 

```

$ sudo service gdm restart
```

instead of rebooting for the time being, as this is faster.


When your mouse's right button stops working, run xev in a terminal, and try right clicking it. Is the right click being detected?

---

### Post by zool--- on 2010-11-11
I got the same issue, it happened after updating to 10.10.

Right mouse button stops working randomly.

Weird.

---

### Post by Solostian on 2010-11-11
I have a similar problem with my left mouse button.
It will start an auto-trigger cycle that ends in it not working.
Right mouse button is fine though.

---

### Post by Solostian on 2010-11-12
The gdm restart gets stuck in the battery scan.

As fer XEV, when the left button stops working, it no longer registers.

Has anyone made progress on this yet? 

For a guy who's trying to move from Windows to Linux, this is really a showstopper...

---

### Post by Ancanus on 2010-11-12
What is your (everyone's) mouse model?

---

### Post by Verbeck on 2010-11-12
there's been some touch-pad issues like this in 10.10. the fix was [http://ubuntuforums.org/showpost.php?p=10083564&postcount=16](http://ubuntuforums.org/showpost.php?p=10083564&postcount=16) . dunno if it'll work for a usb mouse though

---

### Post by zool--- on 2010-11-12
The only label I can see on my mouse is AGM107E. Is an USB device.

I noticed that the right button always stops working after I hit the volume command button on the keyboard. It stuck until I reboot.

---

### Post by Solostian on 2010-11-12
My Mini 9's touch pad has been shot for a while.
I've used two wired optical wheel mice with similar results: a basic Logitech and another one from I.T.Works.

I tried the fix and it did alter the pattern in which the left-button click failure occurs.
It looks as though the click event is delayed. So much so that at some point it never triggers. The right button click works like a charm though.

---

### Post by vanadan on 2010-11-27
hi, I guess I got similar problem. I'm using a notebook (MSI EX600X) and a ordinary cheap usb mouse. Sometimes it happens to me that when I type and accidentaly hit together more keys on the left bottom side of the keyboard (ctrl+alt+shift+whatever - I don't really know what combination causes it, didn't manage to reproduce it) the left mouse button stops working.. when I press the left touchpad button, the mouse usually starts working again, but sometimes doesn't.. :(  unplugging and plugging the mouse again doesn't help, nor trying the keyboard mouse "left button" (ctrl+shift+Numlock, then [/] and [5])

---

### Post by xCasualty on 2010-11-27
> **vanadan said:**
> hi, I guess I got similar problem. I'm using a notebook (MSI EX600X) and a ordinary cheap usb mouse. Sometimes it happens to me that when I type and accidentaly hit together more keys on the left bottom side of the keyboard (ctrl+alt+shift+whatever - I don't really know what combination causes it, didn't manage to reproduce it) the left mouse button stops working.. when I press the left touchpad button, the mouse usually starts working again, but sometimes doesn't.. :(  unplugging and plugging the mouse again doesn't help, nor trying the keyboard mouse "left button" (ctrl+shift+Numlock, then [/] and [5])


I'm using the netbook version as well. Unlike windows, you can not right click on everything. Only in some windows and not the desktop. or does it happen on everything?

---

### Post by blackmonk on 2010-11-27
I have had this problem too - but always after using the extra buttons on my keyboard (volume control I particularly noticed, as I use that a lot). After I had used those buttons the right mouse button would fail to work until I either restarted or unplugged and replugged the keyboard (not the mouse). 

There seems to be a known fault with ubuntu 10.10 with this, and I have seen reports of people having the same problem with kubuntu 10.10. I had no problems like this in kubuntu 10.04, so was disappointed to lose my keyboard shortcuts. 

I found a lot of bug descriptions on this issue in launchpad, but found one that had a work around on this bug discussion that might help some people:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311)

(if that gets shortened and the link stops working, you can search for bug 636311)

Essentially Chris Halse Rogers has posted a link to a xserver package he has set up on a PPA that has a fix to this problem. You can see his PPA here:
[https://launchpad.net/~raof/+archive/aubergine/](https://launchpad.net/~raof/+archive/aubergine/)

This has worked perfectly for me so far - and I am really appreciating having my multimedia keys back.

Considering how many threads there are on this issue here, and on launchpad, I hope this gets an official fix soon.

---

