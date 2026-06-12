---
title: "b43legacy Radio hardware status changed to disabled"
date: 2010-02-06
forum: General Help
---

### Post by shieldie on 2010-02-06
Hi
 
I'm having real problems with Wifi and it's putting me off Linux. Could someone please help me?
 
I'm running Ubuntu 9.10 (no Windows at all on the machine) on an Asus L5800C with Broadcom bcm4303 Wifi.
 
I can't get Wifi to work.
 
Pressing Fn F2 has no effect.
 
I tried following pytheas22's solution on [http://ubuntuforums.org/archive/index.php/t-1066271.html](http://ubuntuforums.org/archive/index.php/t-1066271.html)
 
*cd ~/Desktop*
*tar -xzvf b43_firmware.tar.gz*
*sudo cp -R b43/ /lib/firmware/*
*sudo cp -R b43legacy/ /lib/firmware/*
 
*Then reboot and your wireless should work.*
 
And it did bring up Wifi, although the Wifi indicator on the machine, that worked under Windows XP, did not come on.
 
However, after a minute or so the Wifi stopped working.
 
I looked in the messages log and have an entry that says
kernel: b43legacy-phy0: Radio hardware status changed to DISABLED
 
Help!

---

### Post by shieldie on 2010-02-06
please

---

### Post by shieldie on 2010-02-07
pretty please
 
 
Listen guys, this is the 3rd Wireless card I've had problems with using Linux - 2 with Ubuntu, and 1 with Kubuntu on a really old laptop. [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]
 
[IMG]http://ubuntuforums.org/images/icons/icon5.gif[/IMG]Is there a particular reason why Linux seems to have so much trouble with Wifi whereas Windows does not?
 
Don't get me wrong, I want to use Linux, and I want to move away from Windows, but it's a lot tougher to do than I have been led to believe.

---

### Post by shieldie on 2010-02-08
I don't mean to be a pain, but I'd like to keep this question 'fresh'.
 
Does Wifi with b43legacy actually work under ubuntu 9.10?

---

### Post by shieldie on 2010-02-09
I also tried using: sudo iwconfig wlan0 txpower auto : but that did nothing.
 
The Fn F2 key does change the output of rfkill list. It toggles Soft blocked: from no to yes. However, the indicator on the PC to does switch off and on.
 
Any Linux Wifi geniuses out there to lend a hand?

---

### Post by shieldie on 2010-02-10
Is this problem really so difficult for experts to solve?
 
I hope you're not suggesting I should go back to using WinDOZE!
 
Come on, guys, help me out?
 
I really want to use Linux on my existing machine.
 
Thanks in advance.

---

### Post by untanne on 2010-02-10
Hi,

well I've got the same problem. It looks a little bit tricky, because the log says:"The hardware RF-kill button still turns the radio physically off. Press the button to turn it on."

Log:
> 
Broadcom 43xx-legacy driver loaded [ Features: PLID, Firmware-ID: FW10 ]
Feb 10 15:23:04 L5800 kernel: [ 1557.100098] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
Feb 10 15:23:04 L5800 kernel: [ 1557.106150] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
Feb 10 15:23:04 L5800 kernel: [ 1557.114373] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
Feb 10 15:23:04 L5800 kernel: [ 1557.224047] b43legacy-phy2: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
Feb 10 15:23:04 L5800 kernel: [ 1557.281181] Registered led device: b43legacy-phy2::tx
Feb 10 15:23:04 L5800 kernel: [ 1557.281205] Registered led device: b43legacy-phy2::rx
Feb 10 15:23:04 L5800 kernel: [ 1557.281227] Registered led device: b43legacy-phy2::assoc
Feb 10 15:23:04 L5800 kernel: [ 1557.281250] Registered led device: b43legacy-phy2::radio
Feb 10 15:23:04 L5800 kernel: [ 1557.292431] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 10 15:23:12 L5800 kernel: [ 1565.150525] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb 10 15:23:15 L5800 kernel: [ 1568.000048] b43legacy-phy2: Radio hardware status changed to DISABLED
Feb 10 15:23:15 L5800 kernel: [ 1568.024041] b43legacy-phy2: Radio turned on by software
Feb 10 15:23:15 L5800 kernel: [ 1568.024048] b43legacy-phy2: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
The problem is, I haven't got any switch on my old ASUS L5800C to do this action. It there a software switch somewehere?

Any help would be appreciated.

untanne

Ubuntu 9.10, 32bit, ASUSL5800C

---

### Post by shieldie on 2010-02-10
Hi
 
My problem is slightly different. However, I'm sure my solution (if ever ther is one) will work for you. I'll drop you a message if I get mine to work.
 
I'm going to make a post asking for links to the proprietary Linux and Windows drivers.
 
I'll keep you posted.

---

### Post by shieldie on 2010-02-14
> **untanne said:**
> Hi,
 
well I've got the same problem. It looks a little bit tricky, because the log says:"The hardware RF-kill button still turns the radio physically off. Press the button to turn it on."
 
Log:
The problem is, I haven't got any switch on my old ASUS L5800C to do this action. It there a software switch somewehere?
 
Any help would be appreciated.
 
untanne
 
Ubuntu 9.10, 32bit, ASUSL5800C
 
Well, untanne, I'm now in the exactly the same position as you - getting the same message in the log.
 
I've logged a bug at [http://www.linuxwireless.org/](http://www.linuxwireless.org/).
 
If I get a solution you'll be the first to hear about it.

---

### Post by nostriluu on 2010-03-25
I am trying to help a friend with a Dell Latitude D600 get this system prepared to donate in Cameroon. It has the Broadcom 4306 core 5 chipset and I cannot get it to work - it just shows up as "disconnected." I have tired many solutions and am at wit's end. Any solution would be appreciated.

---

