---
title: "list of devices 10.10"
date: 2011-11-20
forum: General Help
---

### Post by Cool Javelin on 2011-11-20
Hello all:

Does someone know how I can get a list of all the devices I have on my Ubuntu 10.10 machine?

The list should include sound cards, video cards, parallel ports, serial ports, USB, etc....

or

can someone point me to a really good writeup on understanding the hardware devices in a Linux machine?

I just installed another parallel port, but only see one parport0. I DO however see an lp0. Is this the other port?

Also, I now have 2 serial ports, but can't figure out where they show in the /dev directory.

I see sr0, and sr1, but earlier in the list, It looks like there are cdroms linked to those.

Thanks for your help.

Mark.

---

### Post by hal8000 on 2011-11-20
Try the command

lspci

or lspci -v

for a device list. Alternativily install lshw

sudo apt-get install lshw

and 
lshw

to show devices.

---

### Post by lechien73 on 2011-11-20
Have you tried:

```
sudo lshw
```

To list all installed hardware? Serial ports are probably referred to as /dev/tty[X] (where [X] is a number from 0...)

The new parallel port is probably lp0 if your first port is referred to as parport0, but you could try:

```
ls -l lp0
```

Which will help you to see if it's just a link to parport0.

---

### Post by quadproc on 2011-11-20
> **Cool Javelin said:**
> Hello all:

Does someone know how I can get a list of all the devices I have on my Ubuntu 10.10 machine?


You might find some use for the _hardinfo_ program.  If it isn''t already installed on your system then Synaptic can get it for you.  This program will tell you lots and lots of things about your system.

quadproc

---

### Post by Cool Javelin on 2011-11-21
Thank you for these tips

lspci does not list any parallel ports or serial ports. I guess that makes sense as from it's name it would only LiSt PCI devices.

Looks like lshw also doesn't list serial and parallel ports.

I did install hardinfo. That seems pretty good.

Initially, it only showed one parallel port, and 1 serial port (both on the motherboard.)

I went into the BIOS and did a reset of the PCI data, and volarie, I now have 2 of each.

All is well, thanks for your help

Mark.

I have another issue, but is it a slightly different subject, so I will make another post.

---

