---
title: "Installing a UPS serial cable"
date: 2011-01-07
forum: General Help
---

### Post by programmer89 on 2011-01-07
Hey friends! i got this old UPS from compaq long back and installed it with a new battery. Thing is i need to connect it to my PC using this serial cable. But my mobo doest have 1. So i bought a COM port cable converter to serial and have attached the UPS through it.

Now after all this done, my PC wont detect any UPS.. i dont know whether its detecting it or not...

here is the output of dmesg|grep tty

```
stoned_420@stoners ~ $ dmesg|grep tty
[    0.000000] console [tty0] enabled
[    0.852459] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.852698] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

```

So is my UPS being detected :-/ If not how can i know?

Am attaching pics of what all i have.. Hope ya'll can help me and save my UPS from draining off when i'm not at home and theres a power failure :-w

Btw am running x64 10.10

---

### Post by dcstar on 2011-01-07
> **programmer89 said:**
> Hey friend! i got this old UPS from compaq long back and installed it with a new battery. Thing is i need to connect it to my PC using this serial cable. But my mobo doest have 1. So i bought a COM port cable converter to serial and have attached the UPS through it.
..........

Most UPS cables are specially wired for that specific UPS, do you have the special cable?

You may also have to find special Compaq UPS software.

---

### Post by psusi on 2011-01-07
Take a look at [http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/](http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/).

---

### Post by programmer89 on 2011-01-07
How do i know whether my UPS is being detected by the OS through the COM port?

---

### Post by psusi on 2011-01-07
> **programmer89 said:**
> How do i know whether my UPS is being detected by the OS through the COM port?

By installing and configuring nut.

---

### Post by programmer89 on 2011-01-08
> **psusi said:**
> By installing and configuring nut.

Cant get the drivers to work :( I am not even sure whether the com port is detecting my UPS!

Heres the log

```
Jan  8 11:08:41 stoners upscode2[3050]: Missing UPCL after UPCL
Jan  8 11:08:41 stoners upscode2[3050]: No contact with UPS, delaying init.
Jan  8 11:08:43 stoners upscode2[3050]: Missing UPCL after UPCL
Jan  8 11:08:43 stoners upscode2[3050]: No contact with UPS, delaying init.
Jan  8 11:08:45 stoners upscode2[3050]: Missing UPCL after UPCL
Jan  8 11:08:45 stoners upscode2[3050]: No contact with UPS, delaying init.
Jan  8 11:08:46 stoners upsmon[3073]: Poll UPS [server@localhost] failed - Driver not connected
Jan  8 11:08:47 stoners upscode2[3050]: Missing UPCL after UPCL
Jan  8 11:08:47 stoners upscode2[3050]: No contact with UPS, delaying init.
Jan  8 11:08:49 stoners upscode2[3050]: Missing UPCL after UPCL
Jan  8 11:08:49 stoners upscode2[3050]: No contact with UPS, delaying init.
Jan  8 11:08:51 stoners upsmon[3073]: Poll UPS [server@localhost] failed - Driver not connected
Jan  8 11:08:51 stoners upscode2[3050]: Missing UPCL after UPCL
Jan  8 11:08:51 stoners upscode2[3050]: No contact with UPS, delaying init.

```

Btw i am not sure which driver to use for my COMPAQ AVR 500 UPS. I tried choosing powerpanel and upscode2. cyberpower wont load as theres not cyberpower file in /lib/nut!!!

---

### Post by psusi on 2011-01-08
Com ports don't detect anything - UPS or otherwise.  They just send and receive data.  You certainly don't want powerpannel or cyberpower since you don't have a cyberpower brand UPS.  According to the hardware compatibility list in the article I linked before, that compaq model is not supported, but the other compaq models use:

upscode2
upscode2 use_pre_lf
bcmxcp

If one of those doesn't work, then you are probably out of luck.

---

