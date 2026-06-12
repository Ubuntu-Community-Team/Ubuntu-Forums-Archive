---
title: "Wireless switch on Fujitsu Amilo V2000"
date: 2006-03-06
forum: General Help
---

### Post by gumbald on 2006-03-06
After much fighting to try and get my wireless working on my fresh ubuntu install on my laptop, I realised it could be the switch present, and found the following site:

[http://wiki.archlinux.org/index.php/Fujitsu-Siemens_Amilo_Pro2000#WIRELESS_LAN](http://wiki.archlinux.org/index.php/Fujitsu-Siemens_Amilo_Pro2000#WIRELESS_LAN)

Referring to the section on the "kill-switch". I downloaded this and attempted to install, but came across:

```
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
install -d /lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/ipw2100/
install: cannot change permissions of `/lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/ipw2100/': Operation not permitted
make: *** [install] Error 1

```

Should it be even touching the 2100 directory when it's a 2200 chipset? And any suggestions how to get it working, bit of a newbie here :) Wired internet bugging me...

---

### Post by gumbald on 2006-03-07
I cannot find anything else about this online, doesn't seem to be a common laptop, nobody got any ideas?

---

### Post by soonindallas on 2006-03-07
you're right.  you don't need any ipw2100 stuff for a ipw2200 setup.

i'm curious though, because the ipw2200 should work out of the box for ubuntu breezy, except for the LED (which has no impact on wireless networking, but it is a very helpful feedback mechanism for the user...)

specifically, what problem are/were you having ?

---

### Post by soonindallas on 2006-03-07
ok, I looked at your other posts.

do you have a switch/button that toggles your wifi ?  on my laptop it's on the front.

the error message is counter-intuitive: when you see 'kill switch is on' this means your kill switch has deactivated your wifi!

---

### Post by gumbald on 2006-03-07
It appears to be a hardwired switch on this model, which is supposedly supported by the driver from that link. I have found discussions of people getting it to work, but I can't get past the error above... Can't remember which command regarding to the wireless it was, I've been posting in [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623), but it responds with "wireless kill-switch: On". Sorry about the slight vagueness, I've not got my laptop with me at the moment.

---

### Post by gumbald on 2006-03-07
Why would it respond about the permissions of the 2100 folder? Everywhere seems to point to the fsam driver from the mirror in the first link I posted, which is what I tried, to no avail. Is it worth uninstalling all the IPW2200 AND 2100 drivers that may be present in my install?

---

### Post by soonindallas on 2006-03-07
ok.  maybe the linux native ipw2200 driver expects there to be a kill switch for this chipset, but the switch is not present and hardwired as you say.

in any case, you're wasting your time with the ipw2100 driver: it will not work with a ipw2200 chipset.

if wifi works under windows, I suggest you try running the windows driver using ndiswrapper.

though ndiswrapper is supposed to allow linux to use drivers for chipsets with no native linux support, conceptually I suppose you could use it to run the windows driver that works when the native driver does not.  have you tried this ?

there is a wiki page: [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

---

### Post by gumbald on 2006-03-07
As far as I know the Linux driver works, from following the steps in the huge 60+ page thread, just can't turn on the switch because that particular install won't work :(

---

### Post by soonindallas on 2006-03-07
right.  but the windows driver does not seem concerned about this.  try it.  you have nothing to lose, right?

---

### Post by gumbald on 2006-03-07
I'll try the ndiswrapper when I get home and get back to you. Should I remove all the existing 2100 and 2200 drivers using the scripts in the other thread first?

---

### Post by soonindallas on 2006-03-07
[QUOTE=gumbald]I'll try the ndiswrapper when I get home and get back to you. Should I remove all the existing 2100 and 2200 drivers using the scripts in the other thread first?[/QUOTE]

yep.  get rid of it all.

---

### Post by legolas558 on 2008-01-28
The Fujitsu Amilo V2000 is a bulk copy of Maxdata PRO 7000X/DX, see also [HARDWARE Maxdata PRo 7000DX](http://gentoo-wiki.com/HARDWARE_Maxdata_Pro_7000DX).

In order to get it working I do the following commands:
```

modprobe ipw2100
modprobe fsam7400 radio=on
/etc/init.d/net.eth2 start

```

Good luck!

---

