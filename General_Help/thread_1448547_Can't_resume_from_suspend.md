---
title: "Can't resume from suspend"
date: 2010-04-06
forum: General Help
---

### Post by gameguy on 2010-04-06
My laptop won't resume after it suspends. It works fine under win 7 so it's not the hardware. The light says it's on and it's pretty much a blank screen. I'm not sure whether it's operational but the screen is off. It has exactly the same resault a waiting for the blank screen except it won't go back on.

---

### Post by RedSingularity on 2010-04-06
Its a known issue.  I could never get my computer to hibernate or suspend either.  Came across the same problem you have.  I decided to just leave the computer on 24/7 and turn the monitors off when not in use.

---

### Post by gameguy on 2010-04-07
Problem. I'm on a laptop and use sleep all the time .

---

### Post by gameguy on 2010-04-11
Turns out hibernate doesn't work and restart doesn't work either. When I press the power button (set it to ask me) restart isn't an option. If I use the option from the panel it logs out, then stops.

---

### Post by HermanAB on 2010-04-11
Howdy,

Hibernate requires that the size of the swap partition is at least two times the size of the RAM.  That may be your first problem.  Next, you need to have a close look at the system log files to see which drivers do not want to load or unload causing the system to mess up and fix that somehow.

So, some patient sleuthing is required to make it work, but it is not an impossible task, just a very, very, time consuming one.

---

### Post by lvleph on 2010-04-11
Open a terminal and type ```
lsci
``` and then post the output here. Also post the out put from ```
df -h
```. Also, the swap size does not need to be twice the size of the ram, this was an old rule of thumb for performance. To hibernate you will need a swap that is 4GB based on your signature. 

All of these problems can be caused by a broke gnome-powermanager. I actually updated to 10.04, because of powermanager. Now I can suspend and hibernate. However, a proper diagnosis cannot be given without all the proper information.

---

### Post by gameguy on 2010-04-11
The only reason I want Hibernate is cause I keep losing my work cause it runs out of battery due to no suspend. If I get suspend fixed, I don't want Hibernate.

---

### Post by gameguy on 2010-04-11
> **lvleph said:**
> Open a terminal and type ```
lsci
``` and then post the output here. Also post the out put from ```
df -h
```. Also, the swap size does not need to be twice the size of the ram, this was an old rule of thumb for performance. To hibernate you will need a swap that is 4GB based on your signature. 

All of these problems can be caused by a broke gnome-powermanager. I actually updated to 10.04, because of powermanager. Now I can suspend and hibernate. However, a proper diagnosis cannot be given without all the proper information.
lsci not a command. If you mean lspci:
matt@matt-NB:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
14:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
20:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
20:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
20:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
20:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
matt@matt-NB:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda4              40G  6.9G   31G  19% /
udev                  2.0G  328K  2.0G   1% /dev
none                  2.0G  236K  2.0G   1% /dev/shm
none                  2.0G  204K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
none                   40G  6.9G   31G  19% /var/lib/ureadahead/debugfs
/dev/sda2              41G   27G   14G  66% /windows
/dev/sda3             253G  154G   99G  61% /data
//192.168.1.8/$data   269G   54G  215G  20% /server

---

### Post by nodnerb on 2010-06-16
Hi,
Found this thread by googling...

Just a thought - I've had trouble with resume-from-suspend, and found out that if my USB TV tuner (PCTV 73e) is plugged in at the back of my PC, suspend doesn't work properly.

It seems to work if I use the front-mounted USB port (which I think has a different path as the system sees these ports as in a hub).

So, you might want to disconnect your TV tuner (I see from your sig that you have one) and see if that fixes your suspend problems.

Hope that helps,
Brendon

---

### Post by nodnerb on 2010-11-29
Hi,

This thread is probably dead, but here's my solution, logged for completeness.

I followed the suggestion of adding a script in /etc/pm/sleep.d
[here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279143")... and things seem to work well. Now on 10.10.

Hope this helps someone out there!

Brendon

---

### Post by Ollytheninja on 2010-11-29
I also have a solution: adding nohz=off highres=off to my grub config file

---

