---
title: "System Freezes When Downloading Packages"
date: 2006-06-10
forum: General Help
---

### Post by markst on 2006-06-10
Hi All,

I've been impressed with Ubuntu but have had one problem that I just can't seem to  solve.  I have installed Breezy and now Dapper and on both systems whenever I try to dowload an upgrade/package my system freezes part way through.  Here is what I have installed the OS on:

HP Pavilion N3435
AMD K6 Processor running at 533 MHZ
5.0 Gig HD 
256 MB RAM
Maestro sound
Cyberblade video card
Netgear WG511 (Taiwan) PCMCIA card

I think my problems are all associated with the Netgear Card.  With different distros of Linux I have downloaded the fullmac firmware from prism54.org and applied it to the card.  I can't seem to figure out how to do this- or whether I need to with Ubuntu.  Here are the results I get when doing some stuff from the terminal:

ifconfig eth1 says:

eth1      Link encap:Ethernet  HWaddr 00:09:5B:E7:69:44
          inet addr:192.168.2.13  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fee7:6944/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1336518 (1.2 MiB)  TX bytes:268234 (261.9 KiB)
          Interrupt:11

iwconfig says:

lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"dms"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:96:C8:D9:85
          Bit Rate:12 Mb/s   Tx-Power=31 dBm   Sensitivity=20/200
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B
          Link Quality=100/0  Signal level=-76 dBm  Noise level=-178 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

cardctl status says:

Socket 0:
  3.3V CardBus card
  function 0: [ready]

Any help that I can get in helping me solve this issue with freezing is appreciated.  Also, are there log files somewhere that may help pinpoint the problem?  Thanks everyone!

Take care,

Mark:confused:

---

### Post by markst on 2006-06-10
Just to add a bit more info.....I tried downloading some upgrade packages....one at a time.....and I had no failure.  So after each download and installation....I would try downloading one more...and still it worked.  Then I tried downloading the last 3 or 4 together and they worked too.  So I started thinking maybe the problem is solved.

Then I went to add some applications....and selected three or four....and FREEZE part way through one of the downloads.  Had to reboot.  Problem persists.

Then I started wondering if there is a problem with my router or interference from other wireless computers.  I have another Windoze computer that uses a USB Netgear Wireless Adapter running wireless g.  I'm not sure what the PCMCIA card in my laptop is running as....wireless b or g...although the WG511 is capable of g.  Most of the time my desktop is up and running.  Could the router have to switch between g and b and thus cause the Netgear card (if it was running in b) to lock up?

As you can see, I am probably reaching at straws....but I've done all I can think of to solve this problem to no avail.  Your help and advice are appreciated!

Take care,

Mark

:rolleyes:

---

### Post by markst on 2006-06-11
I see I am my own tech support here....but hopefully we get some answer or suggestions soon. 

Could my problems be related to video card or HD settings in the BIOS?  What else should I be looking at?

I downloaded Network Manager Applet and got it working....and I thought that might solve things.  But the problems persists.  Do I need to apply the prism54 fullmac firmware file (ARM) so that the card works better?  How do I do this?

All help is appreciated!

Take care,

Mark

---

