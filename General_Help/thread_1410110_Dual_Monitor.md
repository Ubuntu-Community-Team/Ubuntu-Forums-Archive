---
title: "Dual Monitor"
date: 2010-02-18
forum: General Help
---

### Post by yusbel10 on 2010-02-18
Hello I am new to Ubuntu. I wanted to know how to save the dual monitor using Nvidia X server Manager. I googled how to and it said to delete the "xorg.conf" However I dont have the Permission to delete this file so I would also need to know how to gain full admin access to my Ubuntu Account. Thanks

---

### Post by tom.swartz07 on 2010-02-18
> **yusbel10 said:**
> Hello I am new to Ubuntu. I wanted to know how to save the dual monitor using Nvidia X server Manager. I googled how to and it said to delete the "xorg.conf" However I dont have the Permission to delete this file so I would also need to know how to gain full admin access to my Ubuntu Account. Thanks


Hiya

You have to make sure that your video card is enabled. I dont have too much experience with nVidia cards, but once you get it up and running, theres simply a program that you run from nVidia to get the dual panels up.

You could also try looking in the display settings. system>pref>displays

---

### Post by Jackzor on 2010-02-18
Terminal:

gksudo nvidia-settings

you will be asked for your password.

Give that a try.

And. You never want full root. YOu want temporary root with the sudo 
command. and if you have to use a GUI then for root access you will type the command

gksudo nautilus 

in the terminal.

---

### Post by Jackzor on 2010-02-18
> **tom.swartz07 said:**
> Hiya

You have to make sure that your video card is enabled. I dont have too much experience with nVidia cards, but once you get it up and running, theres simply a program that you run from nVidia to get the dual panels up.

You could also try looking in the display settings. system>pref>displays

Nvidia cards work pretty much out of the box with ubuntu. He needed to open the Nvidia control as sudo. I had the same problem first time I set up dual screens. The gksudo nvidia-settings command should to the trick.

---

### Post by yusbel10 on 2010-02-18
When I hit "Save to X Config File" I get a Failed message saying " Failed to parse exsisting X config file '/etc/X11/xorg.conf'! Even in gksudo terminal.

---

