---
title: "Bluetooth doesn't work"
date: 2011-09-11
forum: General Help
---

### Post by dynjon on 2011-09-11
Hi, I have a lenovo t61 with ubuntu 10.04 LTS. My problem is that I can't get the built in bluetooth working, Fn+F5 turns on/off wifi but nothing happens with bluetooth. On all my previous ibm/lenovos bluetooth has been working at once when I installed ubuntu.
I have read threads where people have had similar problems but nothing has solved my problem.
is there a way to check whether bluetooth really is built in or not?
does anyone have any other suggestions what I could do in order to either get it working or confirmed that I have it built in or not.

---

### Post by gandaran on 2011-09-11
what happens when you click the turn on bluetooth button in bluetooth manager? any error message?

---

### Post by dynjon on 2011-09-11
I tried to open bluetooth manager but I got this message:

Connection to BlueZ failed

Bluez daemon is not running, blueman-
manager cannot continue

---

### Post by gandaran on 2011-09-11
> Connection to BlueZ failed

Bluez daemon is not running, blueman-
manager cannot continue
try this, should fix the problem
```
sudo apt-get remove --purge bluez
```
and then
```
sudo apt-get install bluez
```
purging bluez configuration files and re-installing can fix it, reboot if bluez doesn't start after install.

---

### Post by dynjon on 2011-09-11
It removed the bluetooth manager but still nothing happens when I try to turn on bluetooth.
I don't know if the idea was to remove the bluetooth manager. maybe I did something wrong?

---

### Post by gandaran on 2011-09-11
```

```> **dynjon said:**
> It removed the bluetooth manager but still nothing happens when I try to turn on bluetooth.
I don't know if the idea was to remove the bluetooth manager. maybe I did something wrong?
did you run the commands like I posted? it also removes a couple dependencies but reinstalls them again installing bluez.

try running this command
```
sudo  /etc/init.d/bluetooth  restart
```

---

### Post by dynjon on 2011-09-11
Code:
 	matias@matias-laptop:~$ sudo apt-get remove --purge bluez

[sudo] password for matias: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following packages will be REMOVED:

  blueman* bluez*

0 upgraded, 0 newly installed, 2 to remove and 39 not upgraded.

After this operation, 4,096kB disk space will be freed.

Do you want to continue [Y/n]? y

(Reading database ... 135005 files and directories currently installed.)

Removing blueman ...

Purging configuration files for blueman ...

Removing bluez ...

Purging configuration files for bluez ...

Processing triggers for desktop-file-utils ...

Processing triggers for python-gmenu ...

Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...

Processing triggers for man-db ...

Processing triggers for hicolor-icon-theme ...

Processing triggers for hal ...

Regenerating hal fdi cache ...

Processing triggers for ureadahead ...

ureadahead will be reprofiled on next reboot

Processing triggers for python-support ...

matias@matias-laptop:~$ sudo apt-get instll bluez

E: Invalid operation instll

matias@matias-laptop:~$ sudo apt-get install bluez

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following NEW packages will be installed:

  bluez

0 upgraded, 1 newly installed, 0 to remove and 39 not upgraded.

Need to get 0B/411kB of archives.

After this operation, 1,278kB of additional disk space will be used.

Selecting previously deselected package bluez.

(Reading database ... 134651 files and directories currently installed.)

Unpacking bluez (from .../bluez_4.60-0ubuntu8_i386.deb) ...

Processing triggers for man-db ...

Processing triggers for ureadahead ...

Setting up bluez (4.60-0ubuntu8) ...



matias@matias-laptop:~$ ^C

matias@matias-laptop:~$

---

### Post by dynjon on 2011-09-11
q

---

### Post by dynjon on 2011-09-11
> **gandaran said:**
> did you run the commands like I posted? it also removes a couple dependencies but reinstalls them again installing bluez.

try running this command
```
sudo  /etc/init.d/bluetooth  restart
```


Sorry, I didn't read your last reply carefully enough.

Here is what happened:

Code:

matias@matias-laptop:~$ sudo  /etc/init.d/bluetooth  restart
[sudo] password for matias: 
matias@matias-laptop:~$

---

### Post by gandaran on 2011-09-11
> **dynjon said:**
> Sorry, I didn't read your last reply carefully enough.

Here is what happened:

Code:

matias@matias-laptop:~$ sudo  /etc/init.d/bluetooth  restart
[sudo] password for matias: 
matias@matias-laptop:~$
bluez still not running?

---

### Post by dynjon on 2011-09-11
bluez?
i don't know but bluetooth manager still doesn't appear in system-preferences- and I can't switch on BT and the BT-symbol on the icon bar (between the wireless indicator and the speaker indicator at the top of my desktop) that has always been default on all my previous computers with ubuntu is not there.

---

### Post by dynjon on 2011-09-11
bluez?
i don't know but bluetooth manager still doesn't appear in  system-preferences- and I can't switch on BT and the BT-symbol on the  icon bar (between the wireless indicator and the speaker indicator at  the top of my desktop) that has always been default on all my previous  computers with ubuntu is not there.

---

### Post by gandaran on 2011-09-11
> **dynjon said:**
> bluez?
i don't know but bluetooth manager still doesn't appear in system-preferences- and I can't switch on BT and the BT-symbol on the icon bar (between the wireless indicator and the speaker indicator at the top of my desktop) that has always been default on all my previous computers with ubuntu is not there.
you should still have gnome bluetooth manager in system » preferences but blueman is better (it was removed while removing bluez) so re-install blueman.
```
sudo apt-get install blueman
```

---

### Post by dynjon on 2011-09-11
> **gandaran said:**
> you should still have gnome bluetooth manager in system » preferences but blueman is better (it was removed while removing bluez) so re-install blueman.
```
sudo apt-get install blueman
```


Alright, as far as I am concerned I don't have gnome bluetooth manager but after running

Code:

matias@matias-laptop:~$ sudo apt-get install blueman
[sudo] password for matias: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  blueman
0 upgraded, 1 newly installed, 0 to remove and 39 not upgraded.
Need to get 0B/476kB of archives.
After this operation, 2,818kB of additional disk space will be used.
Selecting previously deselected package blueman.
(Reading database ... 134722 files and directories currently installed.)
Unpacking blueman (from .../blueman_1.21-2ubuntu1_i386.deb) ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up blueman (1.21-2ubuntu1) ...

Processing triggers for python-central ...
matias@matias-laptop:~$

I got bluetooth manager back but I got the same error message as in the beginning i.e.

"Connection to BlueZ failed

Bluez daemon is not running, blueman-
manager cannot continue."

So I guess we are pretty much back where we begun

---

### Post by dynjon on 2011-09-11
Is there a way I can try to run bluetooth manager in the terminal and see what kind of message I get then?

---

### Post by gandaran on 2011-09-11
check if any thing on these threads help
[http://ubuntuforums.org/showthread.php?t=1174624](http://ubuntuforums.org/showthread.php?t=1174624)
[http://www.pclinuxos.com/forum/index.php/topic,77723.0.html](http://www.pclinuxos.com/forum/index.php/topic,77723.0.html)

---

### Post by dynjon on 2011-09-11
Do you still think I have bluetooth built in in the computer or could it be I don't have it?

---

### Post by dynjon on 2011-09-11
alright I'll check

---

### Post by dynjon on 2011-09-11
Thanks anyway for your help :)

---

### Post by gandaran on 2011-09-11
> **dynjon said:**
> Do you still think I have bluetooth built in in the computer or could it be I don't have it?
what do you mean? hardware device?
well for hardware only you know (look up the PC specifications) and if it's broken it's up to you to find out, as for software Ubuntu has everything to run the bluetooth hardware.

---

### Post by dynjon on 2011-09-11
ok, according to the specs I should have the hardware but as you said although I have all software nothing is working so that's just why I was asking

---

### Post by gandaran on 2011-09-11
> **dynjon said:**
> ok, according to the specs I should have the hardware but as you said although I have all software nothing is working so that's just why I was asking
just a thought, maybe Ubuntu 10.04 doesn't have the drivers
run this command and paste the output
```
lspci
```
and
```
lsusb
```

---

### Post by dynjon on 2011-09-11
okay this is what I got 

Code:

matias@matias-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
matias@matias-laptop:~$ 



and

Code:
matias@matias-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 17ef:1003 Lenovo 
Bus 006 Device 002: ID 1199:6813 Sierra Wireless, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
matias@matias-laptop:~$

---

### Post by dynjon on 2011-09-11
after running this command:

Code:
sudo /usr/sbin/bluetoothd start 

I was able to start the bluetooth manager but it is just a blank screen and I can't really do much. I can't turn on/off bluetooth or search for any devices or anything whatever this program is for

---

### Post by dynjon on 2011-09-12
Thanks again for helping, at last I found out what the problem was. Bluetooth was disabled in BIOS...
So it didn't have anything with ubuntu to do at all, sorry.

---

### Post by marstehr on 2011-09-13
> **dynjon said:**
> Alright, as far as I am concerned I don't have gnome bluetooth manager but after running
...

I got bluetooth manager back but I got the same error message as in the beginning i.e.

"Connection to BlueZ failed

Bluez daemon is not running, blueman-
manager cannot continue."

So I guess we are pretty much back where we begun


Try the suggestions given on this link:
[http://www.techtickle.com/recover-missing-networkmanager-applet-blueman-applet.html](http://www.techtickle.com/recover-missing-networkmanager-applet-blueman-applet.html)

Good luck,
Martin

---

