---
title: "Getting lirc to work"
date: 2012-08-04
forum: General Help
---

### Post by Statia on 2012-08-04
Hi all,

I have been trying to get lirc to work. I have a Pinnacle PCTV serial remote. I found the HOWTO on this forum, but I found  it is no longer up to date. (see my posts over there)

What I have done and tried so far:

I run Kubuntu 12.04 with all packages up-to-date.
Lirc version 0.9.0

My motherboard is Asus V6-P8H61ELX. I installed a serial port on the headers for it on the motherboard and enabled the serial port in the BIOS. IO=3F8h, IRQ=4.

```
root@quokka:/home/statia# dmesg | grep ttyS
[    0.873652] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.096725] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.692834] lirc_serial: use 'setserial /dev/ttySX uart none'
```So, that looks like the serial port should be working. Let's execute that setserial command and start lirc:

```
root@quokka:/home/statia# setserial /dev/ttyS0 uart none
root@quokka:/home/statia# service lirc start
 * Starting remote control daemon(s) : LIRC                              [ OK ]
```I had already added lirc_serial to /etc/modules:

```
root@quokka:/etc# lsmod | grep lirc
lirc_serial            19227  0 
lirc_dev               19204  1 lirc_serial
```Now, when trying to get some output from the receiver using irw or mode2 -d /dev/lirc0 (all as root)  I get nothing at all. 
Any ideas?

---

### Post by Statia on 2012-08-04
I am trying to see at which level stuff is not working. If I understand correctly the command

mode2 -d /dev/lirc0

would show the raw data being read by the serial port?
So I hooked up an old serial mouse I dug up from my Museum of Antiquated Hardware and moved and clicked it. No output for mode2. Would this mean the serial port is not yet working?

---

### Post by Statia on 2012-08-07
BUMP and:

```
#dmesg | grep lirc
[73451.547128] lirc_dev: IR Remote Control driver registered, major 250 
[73451.547224] lirc_serial: module is from the staging directory, the quality is unknown, you have been warned.
[73452.446375] lirc_serial: auto-detected active high receiver
[73452.446585] lirc_serial lirc_serial.0: lirc_dev: driver lirc_serial registered at minor = 0

```So the module gets loaded and the receiver seems to get recognized. Still no output for irw, mode2 or -r-keytable though. Anyone an idea for the next step in troubleshooting this?

---

### Post by Statia on 2012-08-08
No one?
I am about to assume my receiver is broken and/or lirc just doesn't work with serial receivers any more and buy me a new remote with USB IR-receiver.

---

### Post by Statia on 2012-08-09
```
$ dmesg | grep serial
[    0.874524] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.547399] lirc_serial: module is from the staging directory, the quality is unknown, you have been warned.
[    3.547616] lirc_serial: port 03f8 already in use
[    3.547630] lirc_serial: use 'setserial /dev/ttySX uart none'
[    3.547631] lirc_serial: or compile the serial port driver as module and
[    3.547633] lirc_serial: make sure this module is loaded first
[    3.547641] lirc_serial: probe of lirc_serial.0 failed with error -16
[    3.547687] platform lirc_serial.0: lirc_dev: driver lirc_serial registered at minor = 0

```Is my kernel grabbing my serial port before the lirc modules can use it?
Can I release it? How?
I have added this line to /etc/rc.local:
```
/bin/setserial /dev/ttyS0 uart none
```Should I load the modules right after that, also from rc.local?
Should I pass a parameter to the kernel at boot not to grab ttyS0?

---

