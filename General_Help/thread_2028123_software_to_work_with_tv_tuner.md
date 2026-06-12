---
title: "software to work with tv tuner?"
date: 2012-07-17
forum: General Help
---

### Post by qwertyjjj on 2012-07-17
Am thinking of getting a usb tv tuner for digital tv on my laptop.
What software can work with something like that in ubuntu?

---

### Post by sanderj on 2012-07-17
> **qwertyjjj said:**
> Am thinking of getting a usb tv tuner for digital tv on my laptop.
What software can work with something like that in ubuntu?

I used to use a DVB-T stick combined with "me-tv".

---

### Post by qwertyjjj on 2012-07-20
got a DV3T DVR stick.
Ubunut seemed to install the drivers but but when I load up Me-TV I still get:
There are no DVB devices available

---

### Post by jimmac49 on 2012-07-20
I use a AverMedia VOLAR DV3T on my laptop, and it works perfectly with Kaffeine,
I have been using it since 9.04 (Jaunty) without any problems, I am now using it on 12.04,
it worked straight out of the box, but on my other laptop running Win 7 I have to use the install disc (What a surprise).

---

### Post by thatguruguy on 2012-07-20
It may be useful to state exactly what usb tv tuner you have.

For instance, I have a [Hauppauge 950Q]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116034"), and it works great. However, not every tuner is supported by Linux.

---

### Post by qwertyjjj on 2012-07-20
> **thatguruguy said:**
> It may be useful to state exactly what usb tv tuner you have.

For instance, I have a [Hauppauge 950Q]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116034"), and it works great. However, not every tuner is supported by Linux.

It's a "Made in CHina" RoHS compliant mini digital TV Stick.
No model number.
Comes with a driver disk but obviously only Windows drivers.

Is there a list if supported tuners?
How can I check if the drivers for this one work ok?

---

### Post by thatguruguy on 2012-07-20
If you would, please type the following commands in a terminal and post the results here.
```
lsusb
``````
dmesg | grep -i dvb
```

---

### Post by thatguruguy on 2012-07-20
> **qwertyjjj said:**
> 
Is there a list if supported tuners?
How can I check if the drivers for this one work ok?

It would be easier to answer that question if you would state where you are, and the TV system you're using.  If you are in Canada, the U.S. or Mexico, here's a listing of [ATSC USB tuners]("http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices"), with a breakdown of support (or lack thereof) in Linux.

---

### Post by qwertyjjj on 2012-07-21
> **thatguruguy said:**
> It would be easier to answer that question if you would state where you are, and the TV system you're using.  If you are in Canada, the U.S. or Mexico, here's a listing of [ATSC USB tuners]("http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices"), with a breakdown of support (or lack thereof) in Linux.

Digital in United Kingdom.
teevee@teevee-Inspiron-9300:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 048d:9135 Integrated Technology Express, Inc. Zolid Mini DVB-T Stick
Bus 003 Device 002: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
teevee@teevee-Inspiron-9300:~$ dmesg | grep -i dvb
[   28.569673] dvb-usb: found a 'ITE 9135 Generic' in cold state, will try to load a firmware
[   29.473418] dvb-usb: did not find the firmware file. (dvb-usb-it9137-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
teevee@teevee-Inspiron-9300:~$

---

### Post by sanderj on 2012-07-21
> **qwertyjjj said:**
> Digital in United Kingdom.
teevee@teevee-Inspiron-9300:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 048d:9135 Integrated Technology Express, Inc. Zolid Mini DVB-T Stick
Bus 003 Device 002: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
teevee@teevee-Inspiron-9300:~$ dmesg | grep -i dvb
[   28.569673] dvb-usb: found a 'ITE 9135 Generic' in cold state, will try to load a firmware
[   29.473418] dvb-usb: did not find the firmware file. (dvb-usb-it9137-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
teevee@teevee-Inspiron-9300:~$

Ah, good: a lsusb ID, and recognized as DVB TV Stick. Good.

As dmesg says: you have to find the firmware. It could be on the accompanied CD, and it probably is somewhere on the web.

I think googling "dvb-usb-it9137-01.fw" will help.

---

### Post by qwertyjjj on 2012-07-21
> **sanderj said:**
> Ah, good: a lsusb ID, and recognized as DVB TV Stick. Good.

As dmesg says: you have to find the firmware. It could be on the accompanied CD, and it probably is somewhere on the web.

I think googling "dvb-usb-it9137-01.fw" will help.

I am trying to run the get_dvb_firmware command but it says not found?
[http://www.linuxtv.org/wiki/index.php/ITE_IT9135](http://www.linuxtv.org/wiki/index.php/ITE_IT9135)

Edit:
So, I managed to do this:
dd if=IT9135BDA.sys ibs=1 skip=69632 count=5731 of=dvb-usb-it9137-01.fw

and copy the fw file to /lib/firmware but how do I get that working now?

---

### Post by sanderj on 2012-07-21
> **qwertyjjj said:**
> I am trying to run the get_dvb_firmware command but it says not found?
[http://www.linuxtv.org/wiki/index.php/ITE_IT9135](http://www.linuxtv.org/wiki/index.php/ITE_IT9135)

It would be useful it you would say what you've done exactly.

[http://www.linuxtv.org/wiki/index.php/Kworld_UB499-2T#Firmware_Instructions](http://www.linuxtv.org/wiki/index.php/Kworld_UB499-2T#Firmware_Instructions) says:


> Locate file get_dvb_firmware in Documentation/dvb of Kernel 3.2 and above.
Run the perl script.
./get_dvb_firmware it9135 


So have you done that?


... Hmmm, OK, let me give you the exact commands as I have the idea that's more useful for you:

```
wget https://raw.github.com/torvalds/linux/master/Documentation/dvb/get_dvb_firmware
perl get_dvb_firmware it9135
```

That should give the firmware, plus the instructions. See below


```
sander@R540:~/Downloads$ wget https://raw.github.com/torvalds/linux/master/Documentation/dvb/get_dvb_firmware
--2012-07-21 11:33:59--  https://raw.github.com/torvalds/linux/master/Documentation/dvb/get_dvb_firmware
Resolving raw.github.com (raw.github.com)... 207.97.227.243
Connecting to raw.github.com (raw.github.com)|207.97.227.243|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 23856 (23K) [text/plain]
Saving to: `get_dvb_firmware'

100%[=====================================================================================================>] 23,856      --.-K/s   in 0.1s    

2012-07-21 11:34:00 (214 KB/s) - `get_dvb_firmware' saved [23856/23856]

sander@R540:~/Downloads$ perl get_dvb_firmware it9135
--2012-07-21 11:34:09--  http://www.ite.com.tw/uploads/firmware/v3.6.0.0/dvb-usb-it9135.zip
Resolving www.ite.com.tw (www.ite.com.tw)... 61.67.129.111
Connecting to www.ite.com.tw (www.ite.com.tw)|61.67.129.111|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9981 (9.7K) [application/x-zip-compressed]
Saving to: `dvb-usb-it9135.zip'

100%[=====================================================================================================>] 9,981       15.4K/s   in 0.6s    

2012-07-21 11:34:10 (15.4 KB/s) - `dvb-usb-it9135.zip' saved [9981/9981]

Firmware(s) dvb-usb-it9135-01.fw dvb-usb-it9135-02.fw extracted successfully.
Now copy it(them) to either /usr/lib/hotplug/firmware or /lib/firmware
(depending on configuration of firmware hotplug).
sander@R540:~/Downloads$ 

```

HTH

---

### Post by qwertyjjj on 2012-07-21
So, I managed to do this manually extracting it from the zip file.
dd if=IT9135BDA.sys ibs=1 skip=69632 count=5731 of=dvb-usb-it9137-01.fw

and copy the 9137-01.fw file to /lib/firmware but how do I get that working now?

---

### Post by sanderj on 2012-07-21
> **qwertyjjj said:**
> So, I managed to do this manually extracting it from the zip file.
dd if=IT9135BDA.sys ibs=1 skip=69632 count=5731 of=dvb-usb-it9137-01.fw

and copy the 9137-01.fw file to /lib/firmware but how do I get that working now?

Is the firmware exact the same as with the method I gave you? Check with "md5sum <firmwarefile>": the hex output should be the same.

If it's the same, unplug the USB TV stick, and plug it in. What does dmesg say? No more complaining about missing firmware?

If so, start me-tv. Choose the country you're in and let it scan (will take about 5 - 10 minutes).

---

### Post by qwertyjjj on 2012-07-21
> **sanderj said:**
> Is the firmware exact the same as with the method I gave you? Check with "md5sum <firmwarefile>": the hex output should be the same.

If it's the same, unplug the USB TV stick, and plug it in. What does dmesg say? No more complaining about missing firmware?

If so, start me-tv. Choose the country you're in and let it scan (will take about 5 - 10 minutes).

```

teevee@teevee-Inspiron-9300:/lib/firmware$ md5sum dvb-usb-it9137-01.fw
b10cbc2921c7d16b1fa90c19d5d6c227  dvb-usb-it9137-01.fw

teevee@teevee-Inspiron-9300:/lib/firmware$ dmesg | grep -i dvb
[   28.569673] dvb-usb: found a 'ITE 9135 Generic' in cold state, will try to load a firmware
[   29.473418] dvb-usb: did not find the firmware file. (dvb-usb-it9137-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[  741.147189] dvb-usb: found a 'ITE 9135 Generic' in cold state, will try to load a firmware
[  741.151695] dvb-usb: did not find the firmware file. (dvb-usb-it9137-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[ 2518.767288] dvb-usb: found a 'ITE 9135 Generic' in cold state, will try to load a firmware
[ 2518.772167] dvb-usb: downloading firmware from file 'dvb-usb-it9137-01.fw'

teevee@teevee-Inspiron-9300:/lib/firmware$ ls -l
total 27732
drwxr-xr-x 32 root root    4096 Apr 23 12:35 3.2.0-23-generic-pae
drwxr-xr-x 32 root root    4096 Jul 16 19:12 3.2.0-26-generic-pae
drwxr-xr-x  2 root root    4096 Apr 23 12:35 3com
drwxr-xr-x  2 root root    4096 Apr 23 12:35 acenic
drwxr-xr-x  2 root root    4096 Apr 23 12:35 adaptec
drwxr-xr-x  2 root root    4096 Apr 23 12:35 advansys
-rw-r--r--  1 root root   50698 Feb 23 19:07 agere_ap_fw.bin
-rw-r--r--  1 root root   65046 Feb 23 19:07 agere_sta_fw.bin
-rw-r--r--  1 root root   22622 Apr  2 20:51 aic94xx-seq.fw
drwxr-xr-x  6 root root    4096 Apr 23 12:35 ar3k
-rw-r--r--  1 root root   70624 Feb 23 19:07 ar7010_1_1.fw
-rw-r--r--  1 root root   70624 Mar 19 18:32 ar7010.fw
-rw-r--r--  1 root root   83968 Feb 23 19:07 ar9170-1.fw
-rw-r--r--  1 root root    3508 Feb 23 19:07 ar9170-2.fw
-rw-r--r--  1 root root   15960 Apr  2 20:51 ar9170.fw
-rw-r--r--  1 root root   51312 Mar 19 18:32 ar9271.fw
drwxr-xr-x  2 root root    4096 Apr 23 12:35 asihpi
-rw-r--r--  1 root root  246804 Apr  2 20:51 ath3k-1.fw
drwxr-xr-x  5 root root    4096 Apr 23 12:35 ath6k
-rw-r--r--  1 root root   30348 Apr  2 20:51 atmel_at76c502_3com.bin
-rw-r--r--  1 root root   31764 Apr  2 20:51 atmel_at76c502.bin
-rw-r--r--  1 root root   31764 Apr  2 20:51 atmel_at76c502d.bin
-rw-r--r--  1 root root   31776 Apr  2 20:51 atmel_at76c502e.bin
-rw-r--r--  1 root root   35180 Apr  2 20:51 atmel_at76c504_2958.bin
-rw-r--r--  1 root root   39928 Apr  2 20:51 atmel_at76c504a_2958.bin
-rw-r--r--  1 root root   31748 Apr  2 20:51 atmel_at76c504.bin
-rw-r--r--  1 root root   31824 Apr  2 20:51 atmel_at76c506.bin
-rw-r--r--  1 root root    9726 Feb 23 19:07 atmsar11.fw
drwxr-xr-x  2 root root    4096 Apr 23 12:35 av7110
drwxr-xr-x  2 root root   12288 Jul 20 12:32 b43
-rw-r--r--  1 root root  114688 May 18 09:09 bcm2033-fw.bin
-rw-r--r--  1 root root    3245 May 18 09:09 bcm2033-md.hex
-rw-r--r--  1 root root 2786404 May 18 09:09 bcm70012fw.bin
-rw-r--r--  1 root root  868372 May 18 09:09 bcm70015fw.bin
drwxr-xr-x  2 root root    4096 Apr 23 12:35 bnx2
drwxr-xr-x  2 root root    4096 Apr 23 12:35 bnx2x
drwxr-xr-x  2 root root    4096 Apr 23 12:35 brcm
-rw-r--r--  1 root root   13424 Apr  2 20:51 carl9170-1.fw
drwxr-xr-x  3 root root    4096 Apr 23 12:35 cis
drwxr-xr-x  2 root root    4096 Apr 23 12:35 cpia2
drwxr-xr-x  2 root root    4096 Apr 23 12:35 cxgb3
drwxr-xr-x  2 root root    4096 Apr 23 12:35 cxgb4
drwxr-xr-x  2 root root    4096 Apr 23 12:35 dabusb
drwxr-xr-x  2 root root    4096 Apr 23 12:35 dsp56k
-rw-r--r--  1 root root      44 May 18 09:09 dvb-cx18-mpc718-mt352.fw
-rw-r--r--  1 root root    9180 May 18 09:09 dvb-dibusb-5.0.0.11.fw
-rw-r--r--  1 root root   32674 May 18 09:09 dvb-fe-cx24116.fw
-rw-r--r--  1 root root    9584 May 18 09:09 dvb-fe-nxt2004.fw
-rw-r--r--  1 root root   12772 May 18 09:09 dvb-fe-or51132-qam.fw
-rw-r--r--  1 root root   17532 May 18 09:09 dvb-fe-or51132-vsb.fw
-rw-r--r--  1 root root    8518 May 18 09:09 dvb-fe-or51211.fw
-rw-r--r--  1 root root   24602 May 18 09:09 dvb-fe-tda10046.fw
-rw-r--r--  1 root root   24878 May 18 09:09 dvb-fe-tda10048-1.0.fw
-rw-r--r--  1 root root   12401 Feb 23 19:07 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root  231952 May 18 09:09 dvb-ttpci-01.fw
-rw-r--r--  1 root root  430328 May 18 09:09 dvb-ttusb-dec-2000t.fw
-rw-r--r--  1 root root  460448 May 18 09:09 dvb-ttusb-dec-2540t.fw
-rw-r--r--  1 root root  465152 May 18 09:09 dvb-ttusb-dec-3000s.fw
-rw-r--r--  1 root root   15913 May 18 09:09 dvb-usb-af9015.fw
-rw-r--r--  1 root root   10757 May 18 09:09 dvb-usb-avertv-a800-02.fw
-rw-r--r--  1 root root    9025 May 18 09:09 dvb-usb-bluebird-01.fw
-rw-r--r--  1 root root   34306 May 18 09:09 dvb-usb-dib0700-1.10.fw
-rw-r--r--  1 root root   33768 Feb 23 19:07 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root    9180 May 18 09:09 dvb-usb-dibusb-5.0.0.11.fw
-rw-r--r--  1 root root    7558 May 18 09:09 dvb-usb-dibusb-6.0.0.8.fw
-rw-r--r--  1 root root    7431 May 18 09:09 dvb-usb-dtt200u-01.fw
**-rw-r--r--  1 root root    5731 Jul 21 10:37 dvb-usb-it9137-01.fw**

```


I'm presuming that the lights on the stick should come on if the firmware is correct.

---

### Post by sanderj on 2012-07-21
My post has three checks / advices. You only fully answered Check #2. How about #1 and #3?

---

### Post by qwertyjjj on 2012-07-21
> **sanderj said:**
> My post has three checks / advices. You only fully answered Check #2. How about #1 and #3?

#1 md5sum asnwreed above
#2 grep answered above
#3 won't work as it still reports missing firmware?
Did you mean those checks?

The firmware is in the /lib/firmware folder?
I'm not sure I fully understand what else I need to do? Your method downloads a 1935 file instead of 1937?

---

### Post by sanderj on 2012-07-21
9135 versus 9137: good point. So I did this:

```
sander@R540:~/Downloads$ perl get_dvb_firmware it9137
Firmware(s) dvb-usb-it9137-01.fw extracted successfully.
Now copy it(them) to either /usr/lib/hotplug/firmware or /lib/firmware
(depending on configuration of firmware hotplug).
sander@R540:~/Downloads$ 
sander@R540:~/Downloads$ ll  dvb-usb-it9137-01.fw 
-rw-rw-r-- 1 sander sander 5731 Jul 21 12:40 dvb-usb-it9137-01.fw
sander@R540:~/Downloads$
sander@R540:~/Downloads$ md5sum dvb-usb-it9137-01.fw
b10cbc2921c7d16b1fa90c19d5d6c227  dvb-usb-it9137-01.fw
sander@R540:~/Downloads$ 
```

Ah, good: only one firmware, and ... with the same size as yours.

Then:
1) your recent message in dmesg looks good, doesn't it? No more "firmware missing"?
Best check: 

remove the usb stick
Then type "tail -f /var/log/syslog"
then press <ENTER> a few times to create some space in the output on your screen
Then plug in the usb stick, and copye-pate the full output from syslog AFTER the empy space into this thread.


2) me-tv: have you started that? I don't see it in your post ... ?

---

### Post by qwertyjjj on 2012-07-21
> **sanderj said:**
> 9135 versus 9137: good point. So I did this:

```
sander@R540:~/Downloads$ perl get_dvb_firmware it9137
Firmware(s) dvb-usb-it9137-01.fw extracted successfully.
Now copy it(them) to either /usr/lib/hotplug/firmware or /lib/firmware
(depending on configuration of firmware hotplug).
sander@R540:~/Downloads$ 
sander@R540:~/Downloads$ ll  dvb-usb-it9137-01.fw 
-rw-rw-r-- 1 sander sander 5731 Jul 21 12:40 dvb-usb-it9137-01.fw
sander@R540:~/Downloads$
sander@R540:~/Downloads$ md5sum dvb-usb-it9137-01.fw
b10cbc2921c7d16b1fa90c19d5d6c227  dvb-usb-it9137-01.fw
sander@R540:~/Downloads$ 
```

Ah, good: only one firmware, and ... with the same size as yours.

Then:
1) your recent message in dmesg looks good, doesn't it? No more "firmware missing"?
Best check: 

remove the usb stick
Then type "tail -f /var/log/syslog"
then press <ENTER> a few times to create some space in the output on your screen
Then plug in the usb stick, and copye-pate the full output from syslog AFTER the empy space into this thread.


2) me-tv: have you started that? I don't see it in your post ... ?

```

Jul 21 11:47:43 teevee-Inspiron-9300 kernel: [  605.719078] usb 1-8: USB disconnect, device number 3



Jul 21 11:48:05 teevee-Inspiron-9300 kernel: [  628.416198] usb 1-8: new high-speed USB device number 4 using ehci_hcd
Jul 21 11:48:05 teevee-Inspiron-9300 kernel: [  628.552631] it913x: Chip Version=02 Chip Type=9135
Jul 21 11:48:05 teevee-Inspiron-9300 kernel: [  628.554127] it913x: Dual mode=0 Remote=5 Tuner Type=ff
Jul 21 11:48:05 teevee-Inspiron-9300 kernel: [  628.555255] dvb-usb: found a 'ITE 9135 Generic' in cold state, will try to load a firmware
Jul 21 11:48:05 teevee-Inspiron-9300 kernel: [  628.560112] dvb-usb: downloading firmware from file 'dvb-usb-it9137-01.fw'
Jul 21 11:48:05 teevee-Inspiron-9300 kernel: [  628.560507] it913x: FRM Starting Firmware Download
Jul 21 11:48:05 teevee-Inspiron-9300 mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8"
Jul 21 11:48:06 teevee-Inspiron-9300 kernel: [  629.072204] it913x: FRM Firmware Download Failed (ffffffed)
Jul 21 11:48:06 teevee-Inspiron-9300 kernel: [  629.272162] it913x: Chip Version=6f Chip Type=0203
Jul 21 11:48:07 teevee-Inspiron-9300 mtp-probe: bus: 1, device: 4 was not an MTP device
Jul 21 11:48:07 teevee-Inspiron-9300 kernel: [  630.108182] it913x: DEV it913x Error


```

Yes, started me-tv and tried kaffeine also but they don't pick up the DVb-T
Me-TV doesn't pick up any channels and Kaffeine won;t allow me to scan as it can't find the USB stick

---

### Post by sanderj on 2012-07-21
You /var/log/syslog shows two interesting parts:


```
it913x: Chip Version=02 Chip Type=9135
```

So ... what is it: an it9135 or an it9137? And what happens when you use the it9135 firmware? There are two 


```
it913x: FRM Firmware Download Failed (ffffffed)
```

Googling that error message gives some (very recent) topics. 
It looks like 913x has been added recently, to kernel 3.2.
Check: which linux kernel do you use? Check with "uname -a"

On [http://forum.ubuntuusers.de/topic/fernseh-schauen-und-aufnehmen-unter-ubuntu/2/](http://forum.ubuntuusers.de/topic/fernseh-schauen-und-aufnehmen-unter-ubuntu/2/) the error message is discussed (special firmware for kernel 3.2, and/or V4L has to be updated),  and the OP tells he'll wait for a few weeks. So no real technical solution there.

When I was trying to get my dvb-usb-stick working, I tried a newer Ubuntu version because of its newer kernel, and that worked. So, if you know how to run a live-Ubuntu-CD/stick, you could try [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) and how things go there.

---

### Post by qwertyjjj on 2012-07-23
> **sanderj said:**
> You /var/log/syslog shows two interesting parts:


```
it913x: Chip Version=02 Chip Type=9135
```

So ... what is it: an it9135 or an it9137? And what happens when you use the it9135 firmware? There are two 


```
it913x: FRM Firmware Download Failed (ffffffed)
```

Googling that error message gives some (very recent) topics. 
It looks like 913x has been added recently, to kernel 3.2.
Check: which linux kernel do you use? Check with "uname -a"

On [http://forum.ubuntuusers.de/topic/fernseh-schauen-und-aufnehmen-unter-ubuntu/2/](http://forum.ubuntuusers.de/topic/fernseh-schauen-und-aufnehmen-unter-ubuntu/2/) the error message is discussed (special firmware for kernel 3.2, and/or V4L has to be updated),  and the OP tells he'll wait for a few weeks. So no real technical solution there.

When I was trying to get my dvb-usb-stick working, I tried a newer Ubuntu version because of its newer kernel, and that worked. So, if you know how to run a live-Ubuntu-CD/stick, you could try [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) and how things go there.

Isn;t 9137 derived from 9135 somhow?
If you look further up the posts, ubuntu definitely says it's looking for the 9137 firmware.
I put the 9135 in the /lib/firmware as well just in case but I don;t think it uses it:
-rw-r--r--  1 root root    8128 Jul 21 11:10 dvb-usb-it9135-01.fw
-rw-r--r--  1 root root    5817 Jul 21 11:10 dvb-usb-it9135-02.fw
-rw-r--r--  1 root root    9981 Aug  4  2011 dvb-usb-it9135.zip
-rw-r--r--  1 root root    5731 Jul 21 11:46 dvb-usb-it9137-01.fw


teevee@teevee-Inspiron-9300:~$ uname -a
Linux teevee-Inspiron-9300 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux

---

### Post by qwertyjjj on 2012-07-23
Right, I gave up on that and bought an AverMedia but now nothing is listed at all in dmesg?
teevee@teevee-Inspiron-9300:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07ca:a835 AVerMedia Technologies, Inc. 
Bus 003 Device 002: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
teevee@teevee-Inspiron-9300:~$ dmesg | grep -i dvb
teevee@teevee-Inspiron-9300:~$ sudo dmesg | grep -i dvb
[sudo] password for teevee: 
teevee@teevee-Inspiron-9300:~$

---

