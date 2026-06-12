---
title: "Latest (couple past) Ubuntu updates killed my Arduino - FTDI connection"
date: 2011-03-08
forum: General Help
---

### Post by dwhitcombe on 2011-03-08
I've been doing linux since downloading slackware diskettes was such a problem that I did it at school, burned the images to a NeXT Magneto-Optical disk, and resurrected those images onto my 386 running DOS 5.0 using my NeXT Cube at home. (just a little cred-establishing-here).
(I could go on)
I have a nice machine, named closet2, that is sitting on my workbench that I use for uploading code to whatever bizarre arduino task I might have in mind at the time. When it's connected to the Arduino's built-in-"/dev/ACM0?" port, it works fine. But when I stick an FTDI cable on the sucker, it does NOT work (or DID NOT work -- I've reached a technologically-impaired workaround).

About 2.5 weeks ago, everything was rosy, the Arduino board (or, more specifically, the boards I'd designed with pin 1 to reset, pin 2 to pin 3 on the chip, pin 3 to pin 2 on the chip, and ground to well... durrr... ground) programmed happily with either an FTDI breakout board from Sparkfun or an FTDI cable from Adafruit. Then came 

   a    K  E  R  N  E  L     U  P  D  A  T  E

Now it's borked.

Totally borked.

I did a lot of frantic googling, and came up with no concrete answer. That's why I'm posting here.

Read that line above if this is too much to read.

When I reloaded the last kernel that worked (2.6.35-24) it worked.


[IMG]http://gendep.com/notes/borked_kernels.png[/IMG]

So... Now..

What to do?

Avrdude can to longer write to my boards (notice the plural -- I've etched with the toner transfer process about 6 boards that have the FTDI header on'em, and no ICSP headers, such hardware re-engineering is a moot point, now)... 

It's the kernel, I think.

The FTDI driver hasn't changed one iota in the interim.

Help? Halp? Hallo?
<tap tap> Is this thing on <tap tap> ?

---

