---
title: "Bluetooth mouse not supported /working"
date: 2009-11-03
forum: General Help
---

### Post by basilwatson on 2009-11-03
Hi

I am trying to get a Microsoft mouse ( bluetooth) to work 

I have followed all the Wikis and documents I can find 

the only way I can get it to work is by command line sudo hidd --connect 00:1B:DC:32:35:31

If I leave it the connection will drop and it will not start on boot up 


I tried Blueman but its wouldn't install even though the dependencies are!!

What do I need to show people ?

Is there a fool proof way to get this to work 


Kind regards 


Stephen

---

### Post by basilwatson on 2009-11-03
bump 

please:D

---

### Post by P4man on 2009-11-03
Have a look here:
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727)

Lots of workarounds in there that may or may not work. Before trying any I would make sure you system is updated as apparently a fix was released recently.

---

### Post by basilwatson on 2009-11-03
Thanks I will work through them after the update!

thank you 


Stephen

---

### Post by walmis on 2009-11-03
> **basilwatson said:**
> Hi

I tried Blueman but its wouldn't install even though the dependencies are!!

Stephen

Could you tell me the errors you encountered ?

---

### Post by basilwatson on 2009-11-03
> **P4man said:**
> Have a look here:
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727)

Lots of workarounds in there that may or may not work. Before trying any I would make sure you system is updated as apparently a fix was released recently.

Sorry no tried everything , its pretty much what I did before 

if I scan it works ok but if I leave it or reboot I hve to rescan ,,,,

any Ideas

Are there any good bluetooth managers out there ?

Stephen

---

### Post by basilwatson on 2009-11-03
> **walmis said:**
> Could you tell me the errors you encountered ?

blueman:
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu5 is to be installed
  Depends: libpango1.0-0 (>=1.21.6) but 1.20.5-0ubuntu1.1 is to be installed
 Depends: libxcb-render-util0  but it is not installable

the first 2 are installed according to synaptic and I cant find libcb-render

I hve tried other repositories , versions etc 

Stephen

---

### Post by John Bean on 2009-11-03
This works perfectly with Jaunty - I had the same issues with a Microsoft 5000 - but I don't know if it's ok in earlier versions. It apparently is not needed for Karmic.

[http://www.serenux.com/2009/08/howto-get-a-microsoft-bluetooth-notebook-5000-mouse-working-under-ubuntu-jaunty/](http://www.serenux.com/2009/08/howto-get-a-microsoft-bluetooth-notebook-5000-mouse-working-under-ubuntu-jaunty/)

---

### Post by walmis on 2009-11-03
> **basilwatson said:**
> blueman:
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu5 is to be installed
  Depends: libpango1.0-0 (>=1.21.6) but 1.20.5-0ubuntu1.1 is to be installed
 Depends: libxcb-render-util0  but it is not installable

the first 2 are installed according to synaptic and I cant find libcb-render

I hve tried other repositories , versions etc 

Stephen

I think you added jaunty PPA repository to Intrepid, you need to add the proper PPA:
The apt entry should look like this:
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) intrepid main

---

### Post by basilwatson on 2009-11-03
> **John Bean said:**
> This works perfectly with Jaunty - I had the same issues with a Microsoft 5000 - but I don't know if it's ok in earlier versions. It apparently is not needed for Karmic.

[http://www.serenux.com/2009/08/howto-get-a-microsoft-bluetooth-notebook-5000-mouse-working-under-ubuntu-jaunty/](http://www.serenux.com/2009/08/howto-get-a-microsoft-bluetooth-notebook-5000-mouse-working-under-ubuntu-jaunty/)

thanks 

but no joy 
The following packages have unmet dependencies:
  blueman: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is to be installed
           Depends: python-gtk2 (>= 2.14) but 2.12.1-0ubuntu1 is to be installed
E: Broken packages

What should I do 

I will have another look

Stephen

---

### Post by John Bean on 2009-11-03
I'd be inclined to add the needed libraries manually, or (better) find a repository that has them; it looks like they don't exist in the usual places for 8.04 judging from the output you posted.

---

### Post by basilwatson on 2009-11-03
not happening at all . 

not with blueman or any other way Ive tried 

any ideas anyone???

Stephen

---

### Post by basilwatson on 2009-11-03
Bump

---

### Post by basilwatson on 2009-11-04
> **John Bean said:**
> I'd be inclined to add the needed libraries manually, or (better) find a repository that has them; it looks like they don't exist in the usual places for 8.04 judging from the output you posted.

Have been trying that , tried ,, Debian but as soon as i download the one I needed its says Idont have another ,,,and so  on 

Nightmare 

I wonder if a dist upgrade would help 

but I have programs on here I dont want to lose or break !

Stephen

---

### Post by basilwatson on 2009-11-04
Bump

---

### Post by walmis on 2009-11-04
As i pointed out earlier you need to add blueman ppa that matches your distribution:
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) YOUR_UBUNTU_VERSION_HERE main

---

### Post by basilwatson on 2009-11-05
> **walmis said:**
> As i pointed out earlier you need to add blueman ppa that matches your distribution:
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) YOUR_UBUNTU_VERSION_HERE main

I have done that &#12540;&#12540;

checked reloaded , tried to install same as before 

Thanks for replying I am lost ......rely am about this mouse 


Stephen

---

### Post by walmis on 2009-11-05
> **basilwatson said:**
> I have done that &#12540;&#12540;

checked reloaded , tried to install same as before 

Thanks for replying I am lost ......rely am about this mouse 


Stephen

could you show me your apt entries?
cat /etc/apt/sources.list

---

### Post by basilwatson on 2009-11-05
in my playing about 
I have managed to kill the usb 

all the other usb devices work but It will not detect the usb dongle 

tried 2 ( same brand unfortunately ) 

Surely it cant be that hard to get a mouse to work 


Honestly I ve tried everything 


Please ,,,, otherwise its the trash bin for a new mouse 

Stephen

---

### Post by P4man on 2009-11-05
> **basilwatson said:**
> in my playing about 
I have managed to kill the usb 

all the other usb devices work but It will not detect the usb dongle 


run ```
lsusb
``` in a terminal. Does it show there? if it does not, then you may indeed have managed to kill it somehow. If it does show up (which I strongly suspect) you have "only" broken bluetooth (in software)

---

### Post by basilwatson on 2009-11-05
> **P4man said:**
> run ```
lsusb
``` in a terminal. Does it show there? if it does not, then you may indeed have managed to kill it somehow. If it does show up (which I strongly suspect) you have "only" broken bluetooth (in software)

caelinux@s-desktop:~$ lsusb
Bus 007 Device 002: ID 04b8:010b Seiko Epson Corp. Perfection 1240
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 046d:08ad Logitech, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 005: ID 1241:1166 Belkin optical mouse w/ scrollwheel
Bus 005 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
caelinux@s-desktop:~

ok havent ,,totally killed it ,,,,but its not flashing and will not connect

Stephen

thanks appreciated that!

---

### Post by P4man on 2009-11-05
Its not flashing because the bluetooth software stack got busted. im pretty sure the stick itself is fine (you can always send it me, I have to buy one anyway :p)

I cant really say what to do as Im hardly (no pun intended) an expert when it comes to bluetooth, but removing and purging all bluetooth packages in synaptic and reinstalling a stack would seem a good bet. Im just not sure which stack.

I would also suggest trying a ubuntu 9.10 live cd and see if that solves your problem, but you will want to test the rest as well before upgrading as it might break other things.

If everything else fails, a logitech MX revolution is a terrific mouse, and works flawlessly (its not bluetooth) :)

---

### Post by basilwatson on 2009-11-06
Gave up installed Ubuntu 9.10 works fine 

Stephen

---

