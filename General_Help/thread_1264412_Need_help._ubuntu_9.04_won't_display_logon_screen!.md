---
title: "Need help. ubuntu 9.04 won't display logon screen! =S"
date: 2009-09-12
forum: General Help
---

### Post by Hoobes1 on 2009-09-12
Hi, recently on ubuntu, it installed some updates. I turned it off and the next morning, when i turned it on, everything was fine. the ubuntu loading screen was there and once it finished loading, something weird happened. the screen turned black with white writing, which looked quite similar to that of the terminal. it said stuff like        can't display logon screen (something like that)         and then it said    daniel@daniel-laptop:~$ and then a command, which i couldn't read, since it then really quickly switched to a black screen with lines on it. the top half of the screen had less, but the bottom half had a couple. The stripes had several colors, mainly white, but also a bit of others. I then turned my pc off, with the button of course, and the same thing happened again when i turned it back on.    Does anyone know how i can solve this? 

thanks

p.s. i'm currently using the live boot cd.

---

### Post by Exodist on 2009-09-12
pop over to a diferent terminal screen using Ctrl+Alt F1 and see if you can login. 
It sounds like xorg has crapped on you. May be due to a update in conjunction with something else on the system possibly associated with the graphics sub system.

Check /etc/X11/xorg.conf and make sure it looks good. 

I would say purge xorg and reinstall it, but that would set off a mammoth size dependency eruption removing everything that using X11, Gnome and everything else not CLI based.

But if you can atleast get to the CLI you move your data and use CDRecord to backup your data and do a quick reinstall wich is faster then bad xorg reinstall idea.. hehe:popcorn:

---

### Post by P4man on 2009-09-12
would it be possible to make a picture of that screen and upload it? I got a hard time figuring out what it is you are seeing.

Another thing you can try, is start without the cd again, in the grub menu select "recovery mode" and then select the "xfix" option to try and repair your X.

---

### Post by Hoobes1 on 2009-09-12
ok. took a picture of what it displays before the stripes appear and the stripes themselves.

---

### Post by zebedeeboss on 2009-09-12
Newbie here but that looks like a screen resolution problem... when ubuntu first boots can u not choose a boot menu and go into something like safe mode and make necessary changes there.

Excuse terminology but I know a similar option is available just don't know exact description yet.

Good luck

---

### Post by P4man on 2009-09-12
Ok, when you get the garbled video, try pressing control+alt+F1.
It should give you a full screen terminal (I hope). log in there with your username and password (the password wont show, just type it and hit enter).

Then try running this:
```
 sudo dpkg-reconfigure xserver-xorg
```

then reboot (you can just enter "sudo reboot" in the terminal).

---

### Post by wojox on 2009-09-12
Got Bluetooth?

---

### Post by Hoobes1 on 2009-09-12
I tried to open up a full screen terminal but when i press ctrl+alt+F1 nothing happens.

---

### Post by P4man on 2009-09-12
> **Hoobes1 said:**
> I tried to open up a full screen terminal but when i press ctrl+alt+F1 nothing happens.

really? Its messed up that badly hmm. You sure lol? I guess control+alt+F2 or F3 dont work either?

Try the other approach I posted above to boot in recovery mode, but it doesn't look good..

---

### Post by Hoobes1 on 2009-09-12
yeah, control+F1 or F2 or F3 don't work, and beforehand with the startup manager, i set up grub to have a time out of 0 seconds. so now i can't choose any of the other boot options. I reset grub a few months ago with the live cd, but don't know how to anymore =S

---

### Post by P4man on 2009-09-12
I thought it was impossible to set grub's delay to <3s. IT doesnt show a "press escape to enter grub menu" either?

If thats the case then, well, indeed boot the live cd. Open a terminal. Type
"gksudo nautilus". Browse to your internal harddrive. find the /boot/grub/menu.lst there (make sure you open it on your harddisk, and not the one from the live session). Open it in gedit (right click, edit) and change the delay to something more than zero. Save, reboot.

---

### Post by Hoobes1 on 2009-09-12
ok, i managed to set grub back to 5 sec timeout. i now booted on ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
what option should i now choose?

---

### Post by P4man on 2009-09-12
you could try a root shell (last option I think, not sure) and enter the commmand I posted a bit up

```
 sudo dpkg-reconfigure xserver-xorg
```

Or you could try the xfix from the recovery menu, though Ive never tried it, and Id try the other first

---

### Post by Hoobes1 on 2009-09-12
ok, so now i've tried out both root promt and xfix but nothing seemed to have happened with both of them. i then tried to login through the root prompt, but that didn't work. Oh and before this happened, and i installed updates, I changed my x so that i could use the graphic card driver for 8.10 since ati doesn't support my card anymore and won't make any drivers for it for 9.04< . could i just make a backup of everything, (menus, docks, home files, etc except for settings such as xorg) and then copy it back onto my ubuntu partition?

---

### Post by wojox on 2009-09-12
Is this a laptop with a usb bluetooth dongle?

Unplug it and reboot if it is.

---

### Post by Hoobes1 on 2009-09-12
> **wojox said:**
> Is this a laptop with a usb bluetooth dongle?

Unplug it and reboot if it is.

it's a laptop with a bluetooth adapter inside it, but i don't know what's a "dongle"

---

### Post by wojox on 2009-09-12
Dongle is the bluuetooth adapter that plugs into the usb port.

---

### Post by Hoobes1 on 2009-09-12
oh ok ^^

---

### Post by wojox on 2009-09-12
Do you have a little switch on the side of your computer to turn on/off wireless?

If so switch it off.

---

### Post by Hoobes1 on 2009-09-12
> **wojox said:**
> Do you have a little switch on the side of your computer to turn on/off wireless?

If so switch it off.

nope, don't have any switch to toggle wireless on/off.

---

### Post by P4man on 2009-09-12
> **Hoobes1 said:**
> , I changed my x so that i could use the graphic card driver for 8.10 since ati doesn't support my card anymore and won't make any drivers for it for 9.04< . 

Oh doh, now you say lol.
What did you do exactly, you tried to downgrade X;org?

Anyway, to get your system somewhat workable again (perhaps), try this in the root shell:

nano /etc/X11/xorg.conf

find the driver section that has "ATI". change it to "vesa"
For instace from:

```
Section "Device"
	Identifier	"something about videocards here"
	Driver		"**ati**"
        Lots more of gibberish
EndSection
```


to :
```

Section "Device"
	Identifier	"something about videocards here"
	Driver		"**vesa**"
        Lots more of gibberish
EndSection
```

Press control X to save, Confirm with Y, reboot cross fingers.
Then back up all your stuff, and prepare for a fresh install. Perhaps stick to 8.10 if you're not planning on buying a new videocard, and if the opensource ATi drivers for jaunty aren't good enough for you.

---

