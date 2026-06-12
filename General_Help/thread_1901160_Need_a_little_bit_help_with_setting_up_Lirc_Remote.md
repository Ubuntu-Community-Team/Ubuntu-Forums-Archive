---
title: "Need a little bit help with setting up Lirc Remote Control.."
date: 2011-12-27
forum: General Help
---

### Post by hopelessone on 2011-12-27
Hi,

I successfully Installed a TV Tuner card:
**ASUS My Cinema-P7131 Hybrid**

I installed Lirc and the remote is supported:[Screen shots]

What is the IR Transmitter in Lirc setup?

All I could find is this:
**IR-Remote: 2.5mm jack**
**Source:** [http://linuxtv.org/wiki/index.php/ASUS_My_Cinema-P7131_Hybrid](http://linuxtv.org/wiki/index.php/ASUS_My_Cinema-P7131_Hybrid)

What should I select? I'm confused...
I tried irw:
> blade@blade-System-Product-Name:~$ irw
connect: Connection refused
blade@blade-System-Product-Name:~$
**Source:** [https://help.ubuntu.com/community/LIRC](https://help.ubuntu.com/community/LIRC)

So I don't really know how to test it..

What am I missing in my steps?

Thanks

---

### Post by hopelessone on 2011-12-28
*bump*

Another guy said: > First it didn't work at all... Then I used SYMLINK irremote catch and setup hardware.conf file. 

IRW works fine! 
Source: [http://ubuntuforums.org/showthread.php?t=1442227&highlight=ASUS+P7131+Hybrid](http://ubuntuforums.org/showthread.php?t=1442227&highlight=ASUS+P7131+Hybrid)

What does he mean, and how can I do that?

and another:> Ok, i figured it out. lirc wasn't looking at the right device. for some reason the IR reciever was at /dev/input/event5, instead of /dev/lirc0 or something. Don't really know why it did it, but reconfiguring lirc worked fine
Source: [http://ubuntuforums.org/showthread.php?t=1336074&highlight=ASUS+P7131+Hybrid](http://ubuntuforums.org/showthread.php?t=1336074&highlight=ASUS+P7131+Hybrid)

I tried reconfiguring, but no go...

What to do?

---

### Post by hopelessone on 2011-12-28
*bump*

> blade@blade-System-Product-Name:~$ sudo dpkg-reconfigure lirc
[sudo] password for blade: 
 * Stopping remote control daemon(s): LIRC                               [fail] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                                     **[COLOR="Red"]Driver `devinpu' not supported.[/COLOR]**
Supported drivers:
	accent
	alsa_usb
	asusdh
	atilibusb
	atwf83


Maybe thats the problem? **Driver `devinpu' not supported.**

---

### Post by hopelessone on 2011-12-28
*bump*

Changed **devinpu** to **devinput** and no go...

Anyone? Anything?

---

### Post by hopelessone on 2011-12-28
Hi,

> Dec 29 11:11:29 blade-System-Product-Name lircd-0.9.0[2911]: caught signal
Dec 29 11:11:29 blade-System-Product-Name lircd-0.9.0[5761]: garbage after 'name' token in line 16 ignored
Dec 29 11:11:29 blade-System-Product-Name lircd-0.9.0[5761]: invalid code found for Asus: Enter
Dec 29 11:11:29 blade-System-Product-Name lircd-0.9.0[5762]: lircd(devinput) ready, using /var/run/lirc/lircd

Does this help any one?

Thanks,

---

### Post by hopelessone on 2011-12-28
HUH?

It works without Lirc? Un-installed Lirc and opened Gedit and works..

Now have to find out how to assign keys to programs...

---

