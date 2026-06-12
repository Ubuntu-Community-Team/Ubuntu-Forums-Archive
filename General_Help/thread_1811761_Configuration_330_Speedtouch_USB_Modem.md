---
title: "Configuration 330 Speedtouch USB Modem"
date: 2011-07-25
forum: General Help
---

### Post by techbrainless on 2011-07-25
Hi All,

I am using ubuntu 10.10 , I have 330 speedtouch usb adsl modem and i want to configure it , 

I have referenced the link [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)
but it has some broken links

I have also checked the post [http://ubuntuforums.org/showthread.php?t=44763](http://ubuntuforums.org/showthread.php?t=44763)
but am not residing in UK

could you suggest me how to configure it

---

### Post by tredegar on 2011-07-25
I threw my speedtouch out about 10y ago - and have never regretted it.
Any (I happen to maintain a load of Netgear stuff - & zero problems) DSL Modem + Ethernet +/- wireless router is the way to go. Installation and maintenance is a breeze. They are not expensive.

But if you are *determined* to use the speedtouch, it *will* work.

Just follow the instructions you have already found. That you do not live in the UK does not matter, you just need to know the correct VP & VC numbers for your ISP. So call your ISP, and ask them what they should be.

So, follow the instructions and let us know (with the exact error messages) if you run into problems. Like I said, it's 10y since I last had to get one of these working, but I expect I'll have some notes somewhere, or maybe just remember the solution when you tell me / us the error message(s).

Good luck.

---

### Post by techbrainless on 2011-07-30
Hi

I have followed the steps given in the post [http://ubuntuforums.org/showthread.php?t=44763](http://ubuntuforums.org/showthread.php?t=44763)
but i did not get connected to the net

here are some of the logs

```
$ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:7b:a2:88:9e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

```
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

```
$tailf /var/log/syslog
Jul 30 19:34:26 test-pc kernel: [ 5431.616053] usb 4-1: USB disconnect, address 4
Jul 30 19:34:43 test-pc kernel: [ 5449.036046] usb 4-1: new full speed USB device using uhci_hcd and address 5
Jul 30 19:34:44 test-pc kernel: [ 5449.848127] usb 4-1: reset full speed USB device using uhci_hcd and address 5
Jul 30 19:34:44 test-pc kernel: [ 5450.040976] speedtch 4-1:1.0: speedtch_find_firmware: no stage 1 firmware found!

```

---

### Post by techbrainless on 2011-07-31
Hi ,
Any reply

---

### Post by tredegar on 2011-07-31
> Jul 30 19:34:44 test-pc kernel: [ 5450.040976] speedtch 4-1:1.0: speedtch_find_firmware: no stage 1 firmware found!

It cannot find the firmware the speedtouch needs.
Did you install it?

---

### Post by techbrainless on 2011-07-31
thanks tredegar for your reply, 

yes i have installed it ,I have executed the command 

```
$sudo dpkg -i speedtouch-firmware_0.3012k_all.deb
```
(off course after downloading the .deb package)

no error was there.

---

### Post by tredegar on 2011-07-31
Well, the error that your distro could not find the firmware to upload to the speedtouch is still there.

So something is still wrong.

I refer you to my post at #2: I threw that speedtouch thing out [It was "given" to me by my windows-orientated ISP]. I had to work very hard to get it to work with linux, when I was very new to linux. On reflection, I see it as a miracle that I ever got it to work at all. With hindsight, I was probably wasting my time, but I learnt some things....

Sometimes the effort required to get something working, just isn't worth the reward. [Unless you are seriously geeky & twisted and your UN of **techbrainless** would suggest otherwise.]

The speedtouch 330 is really old, with badly designed hardware, and not worth the effort.

All recent DSL modem /routers with a cabled or wireless connection, seem to work "out of the box" with linux (see my previous posts).

Learn when the most sensible option is "abandon this quest".

Best wishes.

---

