---
title: "turn on remote desktop via command line"
date: 2010-10-04
forum: General Help
---

### Post by WinterMadness on 2010-10-04
I have to access my laptop and transfer files but the screen is broken. The only protocol that I know for certain that's on that machine is rdp. Since the screen is broken I can't test anythinng else

---

### Post by spiky001 on 2010-10-04
Can explain better is the laptop screen broken or the machine you wanna view???

---

### Post by Tr0w4Tr3y on 2010-10-04
Does your laptop have a external VGA. Maybe you can use other monitor.

---

### Post by WinterMadness on 2010-10-04
> **spiky001 said:**
> Can explain better is the laptop screen broken or the machine you wanna view???

The laptop screen is broken and it is the one I want to view. 

And as far as the VGA thing is concerned will it automatically goto my monitor without telling it to? I've never done it with Linux so I don't know if its auto

---

### Post by Tr0w4Tr3y on 2010-10-04
Since you have a laptop i think all laptops have a function button and the display change option, you can use it to switch between the two monitors or use it at ones. Mind telling me the model of your laptop so we can check it out.?

---

### Post by spiky001 on 2010-10-04
The best way to transfer files would be with a memory stick, otherwise you will need ssh server installed either way you will need a screen as Tr0w4Tr3y has said

---

### Post by WinterMadness on 2010-10-04
> **Tr0w4Tr3y said:**
> Since you have a laptop i think all laptops have a function button and the display change option, you can use it to switch between the two monitors or use it at ones. Mind telling me the model of your laptop so we can check it out.?

Its a pnp7 by system76 I don't know which button to press until I get home I'm at work now. But any and all help is very appreciated

---

### Post by WinterMadness on 2010-10-04
> **spiky001 said:**
> The best way to transfer files would be with a memory stick, otherwise you will need ssh server installed either way you will need a screen as Tr0w4Tr3y has said

The laptop definitely doesn't have an SSH server on it and I can't use a memory stick if I can't see what I'm doing.  This way I can access my computer from another and get the file. Rdp is the only protocol that I know for certain that's on it

---

### Post by endotherm on 2010-10-04
just to clarify, do you mean rdp or vnc? rdp is the windows protocol, whereas the ubuntu default remote desktop protocol is vnc using vino. 

if you wish to enable vnc over the cli (if you have ssh'ed in or somthing) try this tutorial
[http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line](http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line)

it's for an older ubuntu, but shoudl work.

---

### Post by spiky001 on 2010-10-04
as Tr0w4Tr3y said there should be a vga connector on laptop YOU will Need ssh you cant copy files with rdp, even to start anything on laptop you need acsess of some sort

---

### Post by Tr0w4Tr3y on 2010-10-04
Here is a sample keyboard. I encircled the buttons for you to have an idea.

[img]http://img687.imageshack.us/img687/829/delllaptopkeyboard.jpg[/img]

Just press and hold "Fn" and then "F5". (This is for that sample keyboard.)

---

### Post by WinterMadness on 2010-10-04
> **endotherm said:**
> just to clarify, do you mean rdp or vnc? rdp is the windows protocol, whereas the ubuntu default remote desktop protocol is vnc using vino. 

if you wish to enable vnc over the cli (if you have ssh'ed in or somthing) try this tutorial
[http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line](http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line)

it's for an older ubuntu, but shoudl work.

Thanks.



> **spiky001 said:**
> as Tr0w4Tr3y said there should be a vga connector on laptop YOU will Need ssh you cant copy files with rdp, even to start anything on laptop you need acsess of some sort
I dont need ssh, with remote desktop I can control the laptop and since its on the network I can transfer the files and do anything I need to do. 

Yes, I need access. The computer turns on and automatically connects to my network. I just need the command to carefully type.

---

### Post by pricetech on 2010-10-04
The external monitor is probably the best option.  You'll need to be able to see something on the laptop in order to enable any service which might let you remotely control the laptop.

If you can access the files on the laptop with a service that's already running, SSH or Samba for example, then the external monitor may not be needed.

---

### Post by spiky001 on 2010-10-04
the problem is, is desktop sharing enabled on laptop? and setup

---

### Post by spiky001 on 2010-10-04
I have found this [http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line](http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line) will look some more

---

### Post by WinterMadness on 2010-10-04
accidental post

---

### Post by agentr14 on 2012-01-03
just take out the hard drive and get an external case for lie 5 bucks.

---

