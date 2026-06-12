---
title: "On a quest to connect to the internet using a Huawei USB Modem"
date: 2010-05-30
forum: General Help
---

### Post by mindlessbrain on 2010-05-30
Hi all,

So overall I'm happy with my new operating system except that I can't connect to the internet using it. I have a Huawei Sudani one DSL usb modem. I'm running Lucid. 

Sudani One 3.75G Broadband
Model: E1750
HSP USB stick

I've done some things through perusing other threads. I managed to get wvdial installed using the package setup (and several other dependent packages) through the ubuntu website. Same goes for setserial. 

**So I command lsusb and I get:**

jill@jill-desktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0b38:0003  
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. **   <-------- This is my USB Modem/internetz
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Then I tried sudo wvdialconf and it told me: 

Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

**So after installing setserial:**

jill@jill-desktop:~$ setserial
setserial version 2.17, 27-Jan-2000

usage:	 setserial serial-device -abqvVWz [cmd1 [arg]] ... 
	 setserial -g [-abGv] device1 ...

Available commands: (* = Takes an argument)
		(^ = can be preceded by a '^' to turn off the option)
	* port		set the I/O port
	* irq		set the interrupt
	* uart		set UART type (none, 8250, 16450, 16550, 16550A,
			16650, 16650V2, 16750, 16850, 16950, 16954)
	* baud_base	set base baud rate (CLOCK_FREQ / 16)
	* divisor	set the custom divisor (see spd_custom)
	* close_delay	set the amount of time (in 1/100 of a
				second) that DTR should be kept low
				while being closed
	* closing_wait	set the amount of time (in 1/100 of a
				second) that the serial port should wait for
				data to be drained while being closed.
	^ fourport	configure the port as an AST Fourport
	  autoconfig	automatically configure the serial port
	^ auto_irq	try to determine irq during autoconfiguration
	^ skip_test	skip UART test during autoconfiguration

	^ sak		set the break key as the Secure Attention Key
	^ session_lockout Lock out callout port across different sessions
	^ pgrp_lockout	Lock out callout port across different process groups
	^ callout_nohup	Don't hangup the tty when carrier detect drops
				 on the callout device
	^ split_termios Use separate termios for callout and dailin lines
	^ hup_notify	Notify a process blocked on opening a dial in line
				when a process has finished using a callout
				line by returning EAGAIN to the open.
	^ low_latency	Minimize receive latency at the cost of greater
				CPU utilization.
	  get_multiport	Display the multiport configuration
	  set_multiport	Set the multiport configuration

	* rx_trigger	Set RX trigger level (ESP-only)
	* tx_trigger	Set TX trigger level (ESP-only)
	* flow_off	Set hardware flow off level (ESP-only)
	* flow_on	Set hardware flow on level (ESP-only)
	* rx_timeout	Set receive timeout (ESP-only)
	* dma_channel	Set DMA channel (ESP-only)

	  spd_hi	use 56kb instead of 38.4kb
	  spd_vhi	use 115kb instead of 38.4kb
	  spd_shi	use 230kb instead of 38.4kb
	  spd_warp	use 460kb instead of 38.4kb
	  spd_cust	use the custom divisor to set the speed at 38.4kb
				(baud rate = baud_base / custom_divisor)
	  spd_normal	use 38.4kb when a baud rate of 38.4kb is selected

Use a leading '0x' for hex numbers.
CAUTION: Using an invalid port can lock up your machine!
[B]
Then I try sudo wvdialconf again and unfortunately I get:[/B]

jill@jill-desktop:~$ sudo wvdialconf
[sudo] password for jill: 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

**And here I am.** 

I'm at a dead end here, and would really appreciate some help. Everything I need a linux system running for (bioperl) revolves around getting the internet up and running.

Thanks in advance!

---

### Post by mindlessbrain on 2010-05-31
BUMP 

I really need some help for this. Ubuntu will be mostly useless to me if I can't connect to the internet. :(

---

### Post by jimmers on 2010-05-31
Hi mindlessbrain,
Have you tried installing usb-modeswitch it is in Synaptec

Luck

---

### Post by jimmers on 2010-05-31
mindlessbrain,
Try this :-
  	 	 	 	 	 	  [www.betavine.net/bvportal/resources/datacards](www.betavine.net/bvportal/resources/datacards)
 


Luck

---

### Post by mindlessbrain on 2010-05-31
> **jimmers said:**
> Hi mindlessbrain,
Have you tried installing usb-modeswitch it is in Synaptec

Luck

I don't actually know how to install things via synaptec, but I did find the deb package after some googling. I'm trying the vodafone too. Ubuntu does recognize the usb modem as a usb device, so hopefully this will work. 

Thanks! I'll try and report back. =)

---

