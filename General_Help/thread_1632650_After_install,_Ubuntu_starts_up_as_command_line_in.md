---
title: "After install, Ubuntu starts up as command line interface..."
date: 2010-11-28
forum: General Help
---

### Post by Dark Lazer on 2010-11-28
Ok so a little background. I've installed Ubuntu dozens of times. Usually as a dual boot with windows. I'n trying the same thing with a new Sony Vaio laptop I got a few days ago. It says it installs fine, so I boot it up, but I get no GUI, just a command line screen asking me to log in. I can log in fine, but I need the GUI. I didn't do anything different this time than the other times I've installed Ubuntu. 

I did a search and someone suggested using the "startx" command but it just makes my screen go black. Any ideas on what to do? I've been trying for hours and it's getting annoying =\

---

### Post by matt_symes on 2010-11-28
Hi

What graphics card do you have?

You could try

s*udo* dpkg-reconfigure xserver-xorg

*sudo* /etc/init.d/*gdm restart*

Kind regards

---

### Post by sikander3786 on 2010-11-28
We need some more info regarding your hardware including graphics card and RAM.

Try this command and post the output,

Try reconfiguring your graphics as mentioned above.

```
sudo service gdm restart
```

---

### Post by Dark Lazer on 2010-11-28
ok well it's 64-bit (I tried installing both 64-bit ubuntu and 32-bit with the same issue on both). 4 gigs of RAM. The graphics card is just an integrated Intel card.

I tried the:

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm restart

The first command didnt do anything, but the second command made my screen go black again with no other response. I'll try "sudo service gdm restart" an see what happens.

---

### Post by Dark Lazer on 2010-11-28
> **sikander3786 said:**
> We need some more info regarding your hardware including graphics card and RAM.

Try this command and post the output,

Try reconfiguring your graphics as mentioned above.

```
sudo service gdm restart
```

I get "restart: Unknown service:".

---

### Post by sikander3786 on 2010-11-28
> **Dark Lazer said:**
> I get "restart: Unknown service:".
```
sudo service gdm stop
```

```
sudo service gdm start
```

Did you reconfigure the graphics using

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Dark Lazer on 2010-11-28
> **sikander3786 said:**
> ```
sudo service gdm stop
```

```
sudo service gdm start
```

Did you reconfigure the graphics using

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I used the command to reconfigure the graphics and nothing happened, which im assuming is fine? Then I ran the service stop command and it said "stop: unknown service:" but the start command apparently ran something, then my screen went black again. When I say black, I dont mean it shuts off btw, all text just goes away but you can see the screen is still on. 

One thing I did notice is, I hit the power button after it went black, and I got a message saying my resolution was too low or something, and then it shut off. So i restarted it and ran the command again. The screen went black again but now I'm wondering if I should wait a bit? Maybe I stopped it as it was doing something before? not sure, I've never had this happen before.

I really appreciate the help though.

---

### Post by matt_symes on 2010-11-28
Hi

At a terminal type

lshw | grep -A 11 display

and post the output back here. It will tell us a bit about your graphics card.

Kind regards

---

### Post by Dark Lazer on 2010-11-28
> **matt_symes said:**
> Hi

At a terminal type

lshw | grep -A 11 display

and post the output back here. It will tell us a bit about your graphics card.

Kind regards

Sure!

```

[   188.522601 ppdev: user-space parallel port driver
          *-display UNCLAIMED
               description: VGA compatible controller
               product: Core Processor integrated Graphics Controller
               vendor: Intel Corporation
               physical id: 2
               bus info: pci@0000:00:02.0
               version: 02
               width: 64 bits
               clock: 33 MHz
               capabilities: msi pm vga_controller bus_master cap_list
               configuration: latency=0
               resources: memory:f0000000-f03fffff memory:e0000000-efffffff ioport:e080(size=8)

```

The word "display" is in red.

---

### Post by matt_symes on 2010-11-28
Hi

Do you have an xorg.conf file? It might be using the wrong driver. At a terminal type

cat /etc/X11/xorg.conf

and post the results.

> The word "display" is in red.

That is not an issue.

Kind regards

---

### Post by Dark Lazer on 2010-11-28
> **matt_symes said:**
> Hi

Do you have an xorg.conf file? It might be using the wrong driver. At a terminal type

cat /etc/X11/xorg.conf

and post the results.



That is not an issue.

Kind regards
Nope. It says there's no such file or directory when I check.

---

### Post by Dark Lazer on 2010-11-28
Wait I just checked again, and theres a file in there named "xorg.conf.failsafe". not sure why the failsafe, but I opened it and this is what's inside:

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

### Post by matt_symes on 2010-11-28
Hi

> **Dark Lazer said:**
> Wait I just checked again, and theres a file in there named "xorg.conf.failsafe". not sure why the failsafe, but I opened it and this is what's inside:

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Rename the file xorg.conf

sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

and restart. It will try to use the vesa driver.

Kind regards

---

### Post by Dark Lazer on 2010-11-28
> **matt_symes said:**
> Hi



Rename the file xorg.conf

sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

and restart. It will try to use the vesa driver.

Kind regards
Ok I renamed it, restarted Ubuntu, it still booted into the command line interface. I ran "sudo service gdm start" and it booted the GUI! This is progress! Will it boot the GUI from now on or should I make some other changes?

Thank you so much for the help though. I really appreciate it.

---

### Post by Dark Lazer on 2010-11-28
One other problem I've been having is the touch pad doesnt work. It hasent been working at all since installing Ubuntu (works with windows partition). So I've been using the keyboard to navigate as I don't have a spare mouse.

I found this on a different thread on this site:

```


Solution:
For Sony's laptop, edit /boot/grub/grub.cfg, and add these after the kernal line (You should be root):

i8042.reset i8042.nomux i8042.nopnp i8042.noloop

```

But I'm not sure exactly where to add this line. I figured you might be able to point me to exactly where I should add this line, as I dont want to screw up the grub file.

---

### Post by matt_symes on 2010-11-28
Hi

Read this.

[http://fooninja.net/2010/07/29/text-boot-in-ubuntu-lucid-lynx-10-04-disabling-gdm/](http://fooninja.net/2010/07/29/text-boot-in-ubuntu-lucid-lynx-10-04-disabling-gdm/)

You just want to do the converse of what it suggests.

You are still using the vesa driver. It is very useful for debugging. See if there are any drivers for your card.

System->Administration->Hardware drivers

Kind regards

---

### Post by Dark Lazer on 2010-11-29
> **matt_symes said:**
> Hi

Read this.

[http://fooninja.net/2010/07/29/text-boot-in-ubuntu-lucid-lynx-10-04-disabling-gdm/](http://fooninja.net/2010/07/29/text-boot-in-ubuntu-lucid-lynx-10-04-disabling-gdm/)

You just want to do the converse of what it suggests.

You are still using the vesa driver. It is very useful for debugging. See if there are any drivers for your card.

System->Administration->Hardware drivers

Kind regards
Ok well I tried the stuff in the link but I'm not sure I follow. You say to work backwards from what they're saying, but when I go to the files suggested, I'm still a bit lost as to what to change.

Also I couldnt find "Hardware Drivers" in the Administration tab, I did find "Alternate drivers" in a different tab but when I ran it, it found nothing.

---

### Post by matt_symes on 2010-11-29
Hi

Open a terminal and type

cat /etc/default/grub

and post the output back here

Kind regards

---

