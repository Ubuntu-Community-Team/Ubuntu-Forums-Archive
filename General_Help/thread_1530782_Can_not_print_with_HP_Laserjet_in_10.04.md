---
title: "Can not print with HP Laserjet in 10.04"
date: 2010-07-14
forum: General Help
---

### Post by ansiktsburk on 2010-07-14
Hello.
All of a sudden my ubuntu 10.04 can no longer print. I use cups, hp laserjet 1320.
I browse to localhost:631 and add the printer again, it seems to find it alright, but when trying to print it says: "the printer is probably not connected".

```
$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 03f0:1d17 Hewlett-Packard LaserJet 1320

```So it is there, and it have always worked before, but now it has stoped working. What is going on here?

---

### Post by Twinklestorm on 2010-07-15
First I enabled lucid-proposed in synaptic.

Then I did a search on libusb.

I did an update on libusb-0.1-4 from ubuntu0.1 to 0.2.

Disabled proposed again.

Reboot.

Problem fixed for me.

---

### Post by PhysioFixEm on 2010-07-15
Hi! HELP!

Linux newbie-ish(!)  Having very similar problem.  Have been using HP Laserjet 1012 inc printing on Ubuntu (8.10-10.04 inc) with no problems.  A few days ago, printer stopped working.

Linux reports "Printer 'hp-LaserJet-1012' may not be connected.

"lpstat -p && lsusb"  gave the following:

printer hp-LaserJet-1012 now printing hp-LaserJet-1012-0.  enabled since Thu 15 Jul 2010 10:25:48 BST
printer Stylus-Photo-R200 disabled since Fri 30 Apr 2010 22:29:58 BST -
    Unplugged or turned off
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:0d17 Hewlett-Packard LaserJet 1012
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Physical connections are correct.  The printer works as-per-normal under XP (Dual boot - separate hard drive in the same box).

The print jobs just queue for the printer, but seem to get stuck somewhere.

I can't seem to find the hp-toolbox file referred to by Ubuntu help - any idea if it's needed, where to get it, and where it goes (polite answers please!)

As far as I know, my system is totally updated.

Fairly vanilla Ubuntu system - + skype, acrobat reader, flash player etc, and  a few programming tools to help me learn C++

I am really cracking my head with this one.

Have tried the advice above - no avail!

Any suggestions - my wife is grumbling about "this never happens on Windows(!)"?

Many thanks in advance

PhysioFixEm

---

### Post by foresthill on 2010-07-15
Have you tried this:

[http://ubuntuforums.org/showpost.php?p=9570416&postcount=4](http://ubuntuforums.org/showpost.php?p=9570416&postcount=4)

---

### Post by Twinklestorm on 2010-07-16
Did you check syslog?

---

### Post by damagedspline on 2010-08-11
> **foresthill said:**
> Have you tried this:

[http://ubuntuforums.org/showpost.php?p=9570416&postcount=4](http://ubuntuforums.org/showpost.php?p=9570416&postcount=4)

Thanks, worked like a charm!

---

### Post by nerdbird on 2011-04-23
Hello Folks,

Okay, I admit that I am a complete rookie in all of this. And I am the type of guy who doesn't pull over for directions. I was turned on to Linux/ Ubuntu from a friend at my last job. I love it. I have worked through most problems, but I am stumped here. 

I have been having problems printing to my HP Laserjet 1320 since last year. I have tried all of the suggestions I could find. I am left with the printing dialog box showing the print job as "completed" with no action on the printer. I can print the test page using the green button on the printer. I am connected by serial port.

I am trying to print a resume, the printer at the library is chewing up my paper. any help would be greatly appreciated. I don't mind if you are not polite either.:)

---

### Post by JKyleOKC on 2011-04-23
> **nerdbird said:**
> I have been having problems printing to my HP Laserjet 1320 since last year. I have tried all of the suggestions I could find. I am left with the printing dialog box showing the print job as "completed" with no action on the printer. I can print the test page using the green button on the printer. I am connected by serial port.I'm using an HP 1320 also, but mine is connected through the parallel printer port rather than through USB. I'm not aware of a "serial port" connection for it, other than USB.

I originally tried to use the "hplip" package from HP but could not get the printer to work properly. I then switched over to the CUPS interface, used its "Add Printer" wizard, and it's worked correctly ever since.

To get to the CUPS interface, open your web browser and go to [http://localhost:631](http://localhost:631) which will take you to the CUPS home page on your own machine (CUPS is installed automatically with Ubuntu). Select its administration tab, click the "add printer" button, and you're on your way...

---

### Post by nerdbird on 2011-05-03
> **JKyleOKC said:**
> I'm using an HP 1320 also, but mine is connected through the parallel printer port rather than through USB. I'm not aware of a "serial port" connection for it, other than USB.

I originally tried to use the "hplip" package from HP but could not get the printer to work properly. I then switched over to the CUPS interface, used its "Add Printer" wizard, and it's worked correctly ever since.

To get to the CUPS interface, open your web browser and go to [http://localhost:631](http://localhost:631) which will take you to the CUPS home page on your own machine (CUPS is installed automatically with Ubuntu). Select its administration tab, click the "add printer" button, and you're on your way...

Thank you for your response.

I told you I was a total rookie. I _[COLOR=black]am[/COLOR]_ using a parallel printer port. When I go to CUPS, to add new printer (I have deleted my printer to see if I can work from scratch) > Add Printer. Parallel port does not show as an option. It shows:

  Serial Port #1 
 Serial Port #2 

LPD/LPR Host or Printer 
 Internet Printing Protocol (http) 
 Internet Printing Protocol (ipp) 

None are what I am looking for. When I try "find new printers", none are found.  All of my connections are good. I was printing fine up until last year. I am not sure which of the above options I should choose. Not sure where to go from here. Thanks again.

---

### Post by JKyleOKC on 2011-05-04
I would try the "LPD/LPR Host or Printer" choice. On my setup, the printer's connection shows as "Connection:	parallel:/dev/lp0" when I list its properties, but I don't remember just how I got it connected initially.

---

