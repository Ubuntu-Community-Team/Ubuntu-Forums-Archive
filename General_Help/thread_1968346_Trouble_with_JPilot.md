---
title: "Trouble with JPilot"
date: 2012-04-28
forum: General Help
---

### Post by Notre on 2012-04-28
I'm having trouble using JPilot  with the latest Ubuntu, 12.04.  Until recently, I was using the   previous latest  Ubuntu release successfully with JPilot.  Now I am unable to perform synchronization between the palm pilot and my machine.  (Yeah, I know - a palm pilot :)).  It does not recognize the connection as established.  At first, I had trouble synchronizing with the previous version as well, until I learned to change synchronization device preferences from USB to serial (ttyS0), at which point synchronization started working.

I changed synchronization device preferences in 12.04, but unfortunately I'm still unable to establish a connection between the computer and the palm pilot. My next troubleshooting attempt was to issue the following terminal command:

dmesg | grep ttyS

which results in this output:

[    0.344985] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.483696] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A


from this I understand that Linux recognizes my serial port. I don't have another serial device to test with, other than the palm pilot's serial-based cradle. Do you have any suggestions for further troubleshooting?


Thank you,
Notre

---

### Post by Notre on 2012-05-01
I'm embarrassed to say the answer was in the JPilot manual.  I had to do this:

chmod 666 /dev/ttyS0 

and then everything worked.  I didn't do this the first time, at least not explicitly for JPilot but maybe along the way some other program did it, or did it myself for some other reason.

---

### Post by nacho-wan on 2012-05-13
Did you install anything else besides jpilot, jpilot-backup and jpliot-plugins?

---

### Post by StepNjump on 2012-05-15
Hi Notre,

I use a Tungsten T5 (yes, another retro)..
I am experiencing similar problems as you do. For me when under Ubuntu 11.04, it used to work fine for me using : usb: at 115200 bauds.

I tried what you wrote in here the chmod, but nothing works still under U 12.04 32 bits.

Would you mind letting me know?

Thanks in advance,


StepNjump


> **Notre said:**
> I'm embarrassed to say the answer was in the JPilot manual.  I had to do this:

chmod 666 /dev/ttyS0 

and then everything worked.  I didn't do this the first time, at least not explicitly for JPilot but maybe along the way some other program did it, or did it myself for some other reason.

---

### Post by StepNjump on 2012-05-15
Looks like the project is really defunct...

I just wanted to open a bug at [http://bugs.jpilot.org/login_page.php](http://bugs.jpilot.org/login_page.php) and I can't even get my confirmation email so I can open a case....

mmmm

What a waste to buy a new device... the reason I am on linux is specifically because I don't want to litter nature as Windozians do.

---

### Post by celem on 2012-09-13
[QUOTE=StepNjump;11937271]Looks like the project is really defunct...

The jpilot project is NOT defunct, it is simply not very active due to Palm devices waning popularity. I still use a Palm Treo daily and participate in the jpilot mailing list. The mailing list has periodic bursts of activity but is often silent for long periods.

---

