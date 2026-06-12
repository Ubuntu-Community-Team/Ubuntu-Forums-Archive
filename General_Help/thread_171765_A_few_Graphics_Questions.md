---
title: "A few Graphics Questions"
date: 2006-05-07
forum: General Help
---

### Post by gRiMgRaVy014 on 2006-05-07
Is there anyway to disable to integrated video from ubuntu? When I go into the BIOs to option to disable the integrated, the option is there in the instructions, but when I press Enter to change it the only options are "1mb video" and "512k Video" with the disable option no where to be found.

However isn't there another way to chose what graphics card to use?
You chose what port it uses or something liek that? My comp has 3 PCI ports and nothing else, I would put the graphics card on the bottom for maximun air flow. But I'm not sure what PCI port it is or how to set up that option at all, can someone explain this to me?

Thanks!

---

### Post by bluevoodoo1 on 2006-05-07
from a terminal type "lspci" and find the BusID of your new card.

here's an example of my lspci relating to my video card...

0000:02:09.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)


then...

sudo dpkg-reconfigure xserver-xorg

when you get to the screen where it asks for the BusID, type in your new one.

---

### Post by gRiMgRaVy014 on 2006-05-07
Well, thats the problem, most times whenever I put the card in the Ubuntu Logo comes up with it loading all the things farther down in orange, then after that screen, the system freezes and all I see is a frozen underscore.

With this command :sudo dpkg-reconfigure xserver-xorg, could I configure it with out my Nvidia card in , get it all configured to use the nvidia card, then shut down my computer install the card and go from there? Would that work?

---

### Post by bluevoodoo1 on 2006-05-07
[QUOTE=gRiMgRaVy014]With this command :sudo dpkg-reconfigure xserver-xorg, could I configure it with out my Nvidia card in , get it all configured to use the nvidia card, then shut down my computer install the card and go from there? Would that work?[/QUOTE]

Yes that *should* work. But to get the BusID of the PCI slot, might be useful to have the nvidia card in (while working from your other video source).

---

### Post by gRiMgRaVy014 on 2006-05-07
How can I get the bus ID for the card, is it the lspci command?

Is there anyway to select to only load up the command line and not the xserver? That way I should be able to use my graphics card, find the bus number and configure it from there.

---

### Post by bluevoodoo1 on 2006-05-07
yup lspci.

If you have the nvidia card in, but are still using your other means of video, you should be able to grab the BusID... does that freeze your system, or does it freeze only when you try to use the nvidia card?

---

### Post by gRiMgRaVy014 on 2006-05-07
So do you mean plugging the Nvidia card in but plugging the monitor into the integrated card? I can't plug the monitor into the nvidia card, I never get to the login screen, it freezes.

---

### Post by bluevoodoo1 on 2006-05-07
[QUOTE=gRiMgRaVy014]So do you mean plugging the Nvidia card in but plugging the monitor into the integrated card?[/QUOTE]

yes, then you will be able to get your video to work and be able to run lspci--then it will show the BusID of the nvidia card. If you do lspci without the video card in, it won't tell you anything about it.

---

### Post by gRiMgRaVy014 on 2006-05-07
alright I'll try that and post back here if I have any questions thanks.

---

### Post by gRiMgRaVy014 on 2006-05-07
Well I tried putting the graphics card in and then plugging the monitor cable into the integerated slot, all I got was a black screen. So the auto switcher form the BIOs must be doing something. but still, I'm on my integrated graphics right now and when I try to do the command sudo dpkg-reconfigure -phigh xserver-xorg I get this message after my screen goes black for a few seconds:  [B]dane@ubuntu:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.200605071258
[/B]

Not sure what that means, but I do know something, I now can't change what graphics card I want my system to use :-x with out somekind of workaround.

---

### Post by bluevoodoo1 on 2006-05-07
Hmm strange, if you use sudo dpkg-reconfigure -phigh xserver-xorg instead of sudo dpkg-reconfigure xserver-xorg you won't get all of the possible configuration options (Or so I think). 

But still try to get the lspci command to work. That will give you the BusID you need, but again, it will not list your PCI BusIDs if there is nothing plugged into it. 

So.... it seems that if you can get the nvidia card in while having the integrated video work, *then* you should be able to find the PCI bus for the nvidia card. 
Then shutdown, plug in monitor to nvidia card... startup. from the command line... sudo dpkg-reconfigure xserver-xorg, select "nv" driver (later you can install the nvidia driver), type in the correct BusID for nvidia card. Finish the setup... and "startx" (or/and sudo /etc/init.d/gdm restart to get you back to the graphical login)

I hope it can be worked out!

---

### Post by gRiMgRaVy014 on 2006-05-07
Well right now I'm mostly only focusing on finding out that one screen, where you fill ou tthe PCI:0:?:0 thing.I'm nto sure if I put a 3 there or not. I said 3 because I plan on putting the card in the 3rd PCI card slot on my computer.
Do you think I should just put a 3 there, turn off my comp, put in the card and hope it works?

---

### Post by bluevoodoo1 on 2006-05-07
I guess you could just try out a bunch of things... There could also be another number you might need. Again, for example, my card is in the 2nd PCI slot but the BusID is "02:09.0" so I guess you could try a bunch of combinations... "03:00.0" "03:01.0" "03:02.0" "03:03.0" and so on...

Before that, you could also try

sudo lshw

it will give you a listing of your hardware... perhaps it will give you the BusID of the 3rd PCI slot?

---

### Post by gRiMgRaVy014 on 2006-05-07
Well I put my network card into the slot I will be putting my graphics card into and it gave me this 
0000:01:0a.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 01)
 but then I did the command you gave me and it gave me this:
network
                description: Ethernet interface
                product: 82557/8/9 [Ethernet Pro 100]
                vendor: Intel Corporation
                physical id: a
                bus info: pci@01:0a.0
                logical name: eth0
                version: 01
                serial: 00:a0:c9:13:6a:fc
The second one actually gave me a bus info and information about it.
but the beginning of the first one also looks like bus info :
0000:01:0a.0

Do you think I shoudl put those in and hope for the best?

---

### Post by bluevoodoo1 on 2006-05-07
[QUOTE=gRiMgRaVy014]Do you think I shoudl put those in and hope for the best?[/QUOTE]

Yes, try it.

---

### Post by gRiMgRaVy014 on 2006-05-08
Should I put in both of the codes?
Do both of them look like bus info?

---

### Post by bluevoodoo1 on 2006-05-08
[QUOTE=gRiMgRaVy014]Should I put in both of the codes?
Do both of them look like bus info?[/QUOTE]


Well try one combination first, if it doesn't work... then try another. I'm not sure what you mean by putting both in. But it does look like a BusID.

Mine is "0000:02:09.0" but that equates to "PCI:2:9:0" in the sudo dpkg-reconfigure xserver-xorg dialog. (attached screenshot shows correct format)

Since yours says "0000:01:0a.0" you could try it as "PCI:1:0a:0" OR "PCI:1:0:0"

---

### Post by gRiMgRaVy014 on 2006-05-08
If these don't work I will be able to take the card out and reconfigure to the old integrated right?



UPDATE: WEll I tried PCI:1:0:0 and am about to restart, I'm hoping for the best!!!!!!! :D

---

### Post by bluevoodoo1 on 2006-05-16
Have you gotten it working??

---

