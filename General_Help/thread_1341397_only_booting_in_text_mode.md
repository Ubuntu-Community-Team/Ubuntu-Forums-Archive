---
title: "only booting in text mode"
date: 2009-11-29
forum: General Help
---

### Post by willro on 2009-11-29
Ok, so earlier i was having problems with compiz deciding to stop working. so i thought there was a problem with my driver. installed envyng. and ran it in text mode. removed the current driver, installed the envyng driver. and when it asked me to restart i said yes. now upon next reboot it started up all normally, had the white ubuntu logo, then switched to text mode.
so i run through my user name and then password, and doung sudo envyng -t, and installing the driver again, restart, same thing. now i have to boot from the live cd which takes about 900% longer. i have valued information on my filesystem that i'd like to be able to get back to. I'd really like to be able to use the graphic display again.

is my only option to run the live CD and copy all 20gigs of info? and do a reinstall?

how can i solve this without reinstalling?

Ps: this is 9.10

---

### Post by marshag63 on 2009-11-29
One thing you can try is boot into the live cd and copy the xorg.conf to like a USB key or print it or something, then reboot into your install and edit the xorg.conf to match the one when running the live CD.

MarshaG.

---

### Post by lidex on 2009-11-29
So where does it leave you? At a login prompt? Try logging in and then enter command ```
startx
```

---

### Post by willro on 2009-11-29
the startx thing didn't work, came out with something that said no screen found.
 
how would i go about editing the xorg in just a text interface.
 
(somewhere, and computer programmer from the 80's is laughing at me)

---

### Post by lidex on 2009-11-29
Probably easiest to boot LiveCD choosing the option for repairing installation (probably worded differently).

---

### Post by dcstar on 2009-11-29
> **willro said:**
> the startx thing didn't work, came out with something that said no screen found.
 
how would i go about editing the xorg in just a text interface.
 
(somewhere, and computer programmer from the 80's is laughing at me)

```
sudo nano /etc/X11/xorg.conf
```

You will probably find the backup xorg.conf in that folder anyway and you can just rename it and then restart your system.

---

### Post by willro on 2009-11-30
well, as soon as my live CD decides to fully boot rather then just stop at a brown screen with a mouse i'll be sure to try that

the nano editor is confusing the crap out of me also.

---

### Post by lidex on 2009-11-30
> well, as soon as my live CD decides to fully boot rather then just stop at a brown screen with a mouse i'll be sure to try that
You're not getting anything using LiveCD? No boot options?

---

### Post by willro on 2009-11-30
> **lidex said:**
> You're not getting anything using LiveCD? No boot options?
i am, its just after the wait for it to boot from Cd it's just sitting at the brown, pre logon screen. i'll try a few times, if it keeps doing it i'll just burn a copy from an ISO

---

### Post by blueridgedog on 2009-11-30
I would boot to the console and rename your xorg.conf file, then attempt to reboot without one.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.envyng
```

(this command renames your current config to xorg.conf.envyng)

You can either reboot at that point and see what happens, or go ahead and try and reconfigure the xserver:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by willro on 2009-12-01
> **blueridgedog said:**
> I would boot to the console and rename your xorg.conf file, then attempt to reboot without one.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.envyng
```(this command renames your current config to xorg.conf.envyng)

You can either reboot at that point and see what happens, or go ahead and try and reconfigure the xserver:

```
sudo dpkg-reconfigure xserver-xorg
```

marry me?

lol thanks that first line solved it!!! thanks to all those that helped me, now i can submit my Being an American essay among other things.

solved!

---

