---
title: "Belkin N-150 Wireless USB Adapter driver problems"
date: 2011-01-14
forum: General Help
---

### Post by Andrew172 on 2011-01-14
I'm new to Ubuntu, and I'm trying to get my Belkin USB adapter to work. There are plenty of threads already about this, but none really helped me out.

Here's what I've done -

Installed ndiswrapper
Installed ndisgtk
Installed the driver (rt2870.inf) via ndisgtk

ndisgtk reported that the driver was installed and the hardware was present.

The green light on the adapter is solid green, which I assume means that Ubuntu is aware of it's presence. However, when I click the little wireless symbol at the navigation bar, there's no option to choose my adapter (assuming that it's supposed to show up there...)

My adapter version is F6D4050 -

[IMG]http://images17.newegg.com/is/image/newegg/33-314-044-TS?$S300W$[/IMG]

Where do I go from here? I'm a Ubuntu newb, so speak slowly. :D

---

### Post by DanneStrat on 2011-01-14
Andrew and I solved this over email and he got his adapter working on ubuntu 10.04.

The reason it was not working was because his adapter ID was unknown and not yet included in the rt drivers.




So for all of you with an adapter Id of: 050d:935b   

the solution is here: [http://ubuntuforums.org/showthread.php?t=1576001](http://ubuntuforums.org/showthread.php?t=1576001)


Also blacklist rt2800usb




His output of lsusb looks like this:

andrew@ubuntu:~$ lsusb
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 04f9:0229 Brother Industries, Ltd
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:935b Belkin Components
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Andrew172 on 2011-01-14
Done.

---

### Post by DanneStrat on 2011-01-14
Now open a terminal window (applications > accessories > terminal

type this in the terminal and post the output you get

```
lsusb
```

---

### Post by DanneStrat on 2011-01-14
Now open a terminal window (applications > accessories > terminal

type this in the terminal and post the output you get

```
lsusb
```

---

### Post by DanneStrat on 2011-01-14
Alright. Now open a terminal (applications >accessories > terminal

type this in the terminal and post the output you get

```
lsusb
```

---

### Post by DanneStrat on 2011-01-14
Alright. Now open a terminal (applications >accessories > terminal

type this in the terminal and post the output you get

```
lsusb
```

---

### Post by DanneStrat on 2011-01-14
Alright. Now open a terminal (applications >accessories > terminal

type this in the terminal and post the output you get

```
lsusb
```

---

### Post by DanneStrat on 2011-01-14
Now open a terminal (applications >accessories > terminal)

type this in the terminal and post the output you get

```
lsusb
```

It will list all your connected usb devices

---

### Post by DanneStrat on 2011-01-14
Now open a terminal (applications >accessories > terminal)

type this in the terminal and post the output you get

```
lsusb
```

It will list all your connected usb devices

---

### Post by DanneStrat on 2011-01-14
Now open a terminal (applications >accessories > terminal)

type this in the terminal and post the output you get

```
lsusb
```

It will list all your connected usb devices

---

### Post by DanneStrat on 2011-01-14
Now open a terminal (applications >accessories >terminal

type the following in the terminal and post the output you get

```
lsusb
```

This will list all your connected usb devices

---

### Post by DanneStrat on 2011-01-14
Now open a terminal (applications >accessories >terminal

type the following in the terminal and post the output you get

```
lsusb
```

This will list all your connected usb devices

---

### Post by Andrew172 on 2011-01-14
lsusb -
> andrew@ubuntu:~$ lsusb
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 04f9:0229 Brother Industries, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:935b Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

---

### Post by Andrew172 on 2011-01-14
Double post - my bad. The forums are being weird. :P

---

### Post by DanneStrat on 2011-01-14
Now open a terminal (applications >accessories >terminal)

Type the following and post the output you get

```
lsusb
```

This will list all your connected usb devices.

---

### Post by Andrew172 on 2011-01-14
> **DanneStrat said:**
> Now open a terminal (applications >accessories >terminal)

Type the following and post the output you get

```
lsusb
```This will list all your connected usb devices.

andrew@ubuntu:~$ lsusb
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 04f9:0229 Brother Industries, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:935b Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by DanneStrat on 2011-01-14
> **Andrew172 said:**
> Double post - my bad. The forums are being weird. :P

Same for me. There is a private message feature on the forums.

Maybe we can try that instead.

Click "User CP" in the upper left corner and then you 

can send and view messages under the "private messages" tab.

I can post the results here afterwards so others can benefit from 

it.

---

### Post by Andrew172 on 2011-01-14
> **DanneStrat said:**
> Same for me. There is a private message feature on the forums.

Maybe we can try that instead.

Click "User CP" in the upper left corner and then you 

can send and view messages under the "private messages" tab.

I can post the results here afterwards so others can benefit from 

it.

I think I'm having a problem with private messages as well. I reply and I get no errors, but it doesn't list any sent messages or my reply in our conversation thing. =/.

---

### Post by DanneStrat on 2011-01-14
If I send you my email in a private message we can have the 

conversation there instead.

---

### Post by stinkeye on 2011-01-16
...and the result of your Cone of Silence meeting was....

---

### Post by DanneStrat on 2011-01-16
> **stinkeye said:**
> ...and the result of your Cone of Silence meeting was....

I posted the result in the second reply on the first page.

---

### Post by p0o9 on 2011-06-21
050d:935b Belkin Components 
 
I followed the link and implemented the solution to, no wireless connection in
Ubuntu 10.04. However I noticed my device was listed as 935a Belkin and so I changed the references in the solution from "935b" to "935a" BIG MISTAKE!
  I have now lost all USB function in Grub & Ubuntu and since my keyboard is USB I am unable to log on to Linux as I cannot input the password, or to select windows in dual boot system. I have dabbled in linux for 6 mths, but since my network card departed which I replaced with Belkin Usb Wifi, Linux has gone on hold. Wifi in Linux seems to be in the dark ages. I will now have to get a new keyboard, hoping I can log into windows 7 again, and I am currently feeling I should end this Linux experiment for now.

---

