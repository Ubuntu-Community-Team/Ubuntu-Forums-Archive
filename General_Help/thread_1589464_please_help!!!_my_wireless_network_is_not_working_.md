---
title: "please help!!! my wireless network is not working in ubuntu 10.10"
date: 2010-10-06
forum: General Help
---

### Post by jvhellraiser on 2010-10-06
Hi guys.OMG i had to do this because i just updated to ubuntu 10.10 from ubuntu 10.04 and now i can access my wireless network at all the funny part is that with ubuntu 10.04 everything was working perfect so please help me with this cause iam new to this and i dont know how to fix this is not my wireless network cause iam writing to you in windows 7 with my wireless network.

---

### Post by DrReaper on 2010-10-06
Look in the top right corner. Do you see the network connection? You should be able to browse for available networks and select yours. Is there a network icon there?

---

### Post by jvhellraiser on 2010-10-06
well i'll try to explain,iam back to windows 7

well yes the icons for wireless network is there but it wont do nothing i wont read available networks and i try to create one of my networks but it just wont add it at all,once it says that is connected the i open the browser and nothing. but this wont happen in windows 7 and it is the same network.

---

### Post by jvhellraiser on 2010-10-06
> **jvhellraiser said:**
> well i'll try to explain,iam back to windows 7

well yes the icons for wireless network is there but it wont do nothing i wont read available networks and i try to create one of my networks but it just wont add it at all,once it says that is connected the i open the browser and nothing. but this wont happen in windows 7 and it is the same network.


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by Abanabanana on 2010-10-10
hi
same problem with me, 10.10 jsut doesnt recognize my wlan usb devices... and i already tried several....

the old version did recognize them immediatly..

some hints?

cheers

---

### Post by antwerp-avp on 2010-10-11
the same problem on my Asus EEE PC 901

---

### Post by jlow00 on 2010-10-11
I have the same problem with the Intel 5300 wireless card on my Lenovo x200.  This works perfectly with 10.04 and 9.10 but not any longer with 10.10.  I'm not sure what the problem is but it's not the hardware.  I'm going to stick it out for a week before I officially roll back.  This is with the non beta 10.10 too BTW.

---

### Post by Quackers on 2010-10-11
Can you connect to the router using an ethernet cable then go to System > Admin > Additional Drivers. It may be that the required drivers will be downloaded then - possibly.

---

### Post by fusionhead on 2010-10-11
> **jvhellraiser said:**
> Hi guys.OMG i had to do this because i just updated to ubuntu 10.10 from ubuntu 10.04 and now i can access my wireless network at all the funny part is that with ubuntu 10.04 everything was working perfect so please help me with this cause iam new to this and i dont know how to fix this is not my wireless network cause iam writing to you in windows 7 with my wireless network.

I've done a lot of these and got all of them working.  What I do is:

1) Connect an Ethernet cable to your laptop or system to your router, don't use wireless.  I know that you already installed it, just read on and try it with the cable and go to step 3.

2) Install Ubuntu wubi or install cd.  

3) After the install, go to the System-Administration Pull-down Menu and find Hardware Drivers. It looks for proprietary drivers that Ubuntu is not legally allowed to include so you have to do this manually. It should find something like STA Wireless Driver. Select it.  If there are more than one, pick the recommended one and enable it.  While you are there, if there is a driver for your video card, enable that too while you are at it (then after step 4, go into System-Preference-Appearance and select extra under visual.  I know this is outside of what you asked for but while you are there, do it).

4) Reboot and your wireless should now be working.

---

### Post by jlow00 on 2010-10-11
Going to the System > Administration > Additional Drivers shows nothing, at least for me and an Intel 5300 Wireless card.:confused:

---

### Post by fusionhead on 2010-10-11
> **jlow00 said:**
> Going to the System > Administration > Additional Drivers shows nothing, at least for me and an Intel 5300 Wireless card.:confused:

Bummer.  You could also try to use another wired/wireless manager.  I use wicd

```
%sudo aptitude install wicd
```

---

### Post by Quackers on 2010-10-11
> **jlow00 said:**
> Going to the System > Administration > Additional Drivers shows nothing, at least for me and an Intel 5300 Wireless card.:confused:


Did you plug in an ethernet cable first?

---

### Post by jlow00 on 2010-10-11
I did plug in directly to the router, wired networking works fabulously.  While connected via wired eth0 (internet browsing working and all) I went to the additional drivers and nothing appeared as available.  

I would be interested if the person that started this thread is the same way.  

When I do this same thing on my big desktop system with ubuntu 10.04 (completely different system), I get the Nvidia drivers appear for my video card so I know what to look for.  My notebook (Lenovo X200) has the Intel 5300 wireless adapter that DOES work under 10.04 (yay).  Perhaps I'll go back to 10.04 on my notebook here and see what Additional drivers appear as a comparison.

---

### Post by sgwebb on 2010-10-11
This could be the same issue as this resolved post .. 
[http://ubuntuforums.org/showthread.php?t=1592866](http://ubuntuforums.org/showthread.php?t=1592866)

---

### Post by Hakunka-Matata on 2010-10-11
```
rfkill list
sudo rfkill unblock all
rfkill list
```

That's probably from the thread # shown by the previous responder

---

### Post by Hakunka-Matata on 2010-10-11
```
rfkill list
sudo rfkill unblock all
rfkill list
```

That's probably from the thread # show by the previous responder
edited: It is indeed from the post from P4man

Thanks P4man, I love discovering code like this,

---

### Post by jlow00 on 2010-10-11
> **Hakunka-Matata said:**
> ```
rfkill list
sudo rfkill unblock all
rfkill list
```

That's probably from the thread # shown by the previous responder

This doesn't seem to be the same issue, i tried though:


from lspci:
03:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300

This is what it looks like without me changing anything:
sudo rfkill list

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Then I give it a go:
sudo rfkill unblock all

sudo rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

no changes:(

---

### Post by jlow00 on 2010-10-12
looks like all is well for me after changing from "N only" on my router to "mixed mode" [http://ubuntuforums.org/showthread.php?t=1592846]("http://ubuntuforums.org/showthread.php?t=1592846")

---

### Post by fusionhead on 2010-10-12
> **jlow00 said:**
> looks like all is well for me after changing from "N only" on my router to "mixed mode" [http://ubuntuforums.org/showthread.php?t=1592846]("http://ubuntuforums.org/showthread.php?t=1592846")

Glad you got it working!  Just curious, when you were having problems, were you seeing SSIDs of yours and other networks?

---

### Post by jlow00 on 2010-10-13
Yes I was able to see mine and other SSID's in my neighborhood prior with the N only setting.  I guess if I want "N only" I could simply delete the /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf file in my case as per the above mentioned thread.  I'm not sure why it's there in the first place. Oh well.  Cheers:)

---

### Post by golbasche2 on 2010-10-15
My wireless worked on 10.04 but stopped working after 10.10 upgrade. Lenovo W500. Intel 5300 card.


I tried changing to "N only" as described in earlier posts. No success.

I tried running the rfkill commands. No success.

When I click the Network Manager icon in my panel, I see that my wired connection is working, but below Wireless networks, it says "wireless is disabled". 

Fortunately, I did find that ```
$ sudo ifconfig wlan0 up
``` turns my wireless indicator on. That is all though. It only turns on the LED.

Any ideas?

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.
```


```
$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no 
```

```

$ zgrep iwl /var/log/messages
Oct 14 17:55:50 kevin-laptop kernel: [    2.782803] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Oct 14 17:55:50 kevin-laptop kernel: [    2.782805] iwlagn: Copyright(c) 2003-2010 Intel Corporation
Oct 14 17:55:50 kevin-laptop kernel: [    2.782881] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 14 17:55:50 kevin-laptop kernel: [    2.782960] iwlagn 0000:03:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
Oct 14 17:55:50 kevin-laptop kernel: [    2.823435] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Oct 14 17:55:50 kevin-laptop kernel: [    2.856404] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12

```

---

### Post by jlow00 on 2010-10-16
Delete the file as per post #20 /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf and reboot.  This works for me now with the N only setting, or any setting for that matter.  The rumor is this file is an artifact from testing in the OS development.

---

### Post by golbasche2 on 2010-10-16
double post

---

### Post by golbasche2 on 2010-10-27
> **golbasche2 said:**
> Thanks. I tried that already and it didn't work. For kicks, I tried it again and got the same result ("wireless is disabled"). Fortunately I hardly ever need to use wireless, so I'll check the forums in a month from now hoping that someone has a solution. Maybe I'll get lucky and an update will magically fix everything.

EDIT: It must have been network-manager that got messed up. Wicd works great. I'm too lazy to figure out what was actually going wrong with network-manager, so I'll stick with Wicd.

EDIT2: Reinstalled network manager. Problem solved.

---

### Post by imran_e on 2011-01-02
Goto synaptic manager. The bcmwl drivers is marked as required as update required. Update the bcmwl drivers and it works.

Running on a Dell inspiron 14R. Upgraded from 10.04 to 10.10 via an alternate CD.

---

