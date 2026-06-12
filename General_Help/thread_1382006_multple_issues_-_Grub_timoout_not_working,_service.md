---
title: "multple issues - Grub timoout not working, services not auto starting"
date: 2010-01-15
forum: General Help
---

### Post by jwvraets on 2010-01-15
Been having a frustrating time  the last while with Ubuntu Karmic 64-bit (fully updated) on  2 systems. Common to both:

CPU - AMD Athalon II quadcore
MOBO - Gigabyte MA785GMT-UD2H

 Differences:
on Atilla:
------------
RAM - 4 gig
Dual Boot _XP and Ubuntu
HD - 500gig for XP and 1.5T for Ubuntu

On Fourpak:
-------------
RAM - 8 gig
dedicated ubuntu
HD - 1 T dedicated ubuntu

Issues:
---------
1. Both systems - GRUB does not auto timeout to default and you need to manually hit Enter to get the "default" (or select and hit Enter) to get the os to boot. Timeout does not work and editing the timeout values as recommended in the grub documentation has absolutely no impact.

2. Both systems - Services do not automatically start up. For example neither SSH nor CUPS absolutely startup regardless of anything I can do (and I an becoming suspicious that no other services will either). However, a manual start using 
   sudo /etc/init.d/ssh restart  (or cups)
works properly.

By comparison, a third system (tophat) running Ferdora 12 works just fine.

I suspect a bug of some type in grub and/or possibly upstart. But in the meantime I need to get this stuff autostarting and the services starting up automatically. Hunting around online has not been fruitful. 

Does anyone have a similar experience? If so has anyone found a fix or a viable workaround to deal with the GRUB timeout issue and the services startup issue. Help would be VERY welcome.

JW

---

### Post by Leppie on 2010-01-15
> **jwvraets said:**
> 1. Both systems - GRUB does not auto timeout to default and you need to manually hit Enter to get the "default" (or select and hit Enter) to get the os to boot. Timeout does not work and editing the timeout values as recommended in the grub documentation has absolutely no impact.
some systems seem to always set the recordfail variable to be true. a workaround is disabling the checking of the variable in the 00_header file. open the file:
```
gksudo gedit /etc/grub.d/00_header
```
comment out the last if statement like this:
```
#if [ \${recordfail} = 1 ]; then
#  set timeout=-1
#else
  set timeout=${GRUB_TIMEOUT}
#fi
```
do not comment out the normal set timout line in the if statement (this will leave you without timer as well). save and exit, then run update-grub:
```
sudo update-grub
```

> **jwvraets said:**
> 2. Both systems - Services do not automatically start up. For example neither SSH nor CUPS absolutely startup regardless of anything I can do (and I an becoming suspicious that no other services will either). However, a manual start using 
   sudo /etc/init.d/ssh restart  (or cups)
works properly.
try installing sysv-rc-conf:
```
sudo apt-get install sysv-rc-conf
```
in my system cups is not started by upstart, but i believe upstart starts the sysv system which in turn launches cups. this may also be true for the ssh daemon.

---

### Post by jwvraets on 2010-01-15
Leppie: 
Thank you for your help. I have half of my problem solved now.

The GRUB suggestion works perfectly.  Thank you very much.


The problem with the startup of service, SSH and CUPS did not respond to your suggestion, however. So I am still looking for a solution or workaround for this element. If you have any other ideas, they would be much appreciated. If anyone else has any ideas, suggestions that would also be welcome, of course.

Meanwhile Leppie, regardless of how this works out, if you are ever up my way I owe you a beverage of choice. Thanks again for some good news as the week ends.

JW

---

### Post by jwvraets on 2010-01-15
I came across this discussion:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/437905](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/437905)

which seems to suggest some underlying issues related to managing services under Karmic. Does anyone have some insight they could share on this and whether it is related to the issues I am having getting SSH and CUPS to startup automatically on system startup?

---

### Post by Leppie on 2010-01-15
i think it's more related to this bug: [https://bugs.launchpad.net/ubuntu/+bug/444597](https://bugs.launchpad.net/ubuntu/+bug/444597)

maybe a silly question, but have you checked the cups script? and maybe the dmesg log can shed some light on this:
```
less /var/log/dmesg
```

---

### Post by Leppie on 2010-01-15
> **jwvraets said:**
> Meanwhile Leppie, regardless of how this works out, if you are ever up my way I owe you a beverage of choice. Thanks again for some good news as the week ends.
thanks, i'll keep that in mind. keep one cold for me then ;)

---

### Post by jwvraets on 2010-01-21
Just a follow up on the services portion of the issues I listed at the start of this thread....

Another thread has provided a workaround to getting the services to start automatically on my systems. The relevant message is from j23tom and appears as message #27 in the thread at:

        [http://ubuntuforums.org/showthread.php?t=1305226&page=3](http://ubuntuforums.org/showthread.php?t=1305226&page=3)

In essence the workaround posted by j23tom is (and I quote):

=============================
 				 				**Re: 9.10 Upstart Breaks Cron,Cups,SSH, etc...** 			
 			 			 		   		 		 		Check if you have loopback interface in:
/etc/network/interfaces

there should be (at file top):
auto lo
iface lo inet loopback

After I've added this, my services were back
=============================

I can confirm the above does work for the services I have been having trouble with, specifically: ssh, cups and mysql

I hope j23tom's fix helps out any other poor soul dealing with that issue.

Cheers

JW

---

