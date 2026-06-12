---
title: "Wireless dropping"
date: 2009-07-21
forum: General Help
---

### Post by mancrow on 2009-07-21
I installed the new ubuntu 9.04 on my laptop and when am using the wireless card it drops the connection. it will still be connected but the internet wont work. The wireless works fine in windows and older versions of ubuntu. The internet will work but it will fade in and out all the time and i have to use a hard line to use the internet without it dropping every 2 minutes.

any help would be great.

Its a dell inspiron 1720 with a dell mini card wifi G card

thanks.

---

### Post by mancrow on 2009-07-22
Bump !

---

### Post by nothingspecial on 2009-07-22
Some people have found that installing linux-backports-modules-2.6.28-13-generic and wicd have solved this problem.

Not in my case though.

---

### Post by cooper77z on 2009-07-22
lol :lolflag: I thought you said wireless eavesdropping! I think you could correct it if you installed your driver in a better fashion. My wireless connection always dropped in XP. My ethernet connection never drops in ubuntu. Me thinks wireless connections just drop and then you have to connect again. Lot's of atmospheric conditions in the air.

---

### Post by mancrow on 2009-07-23
Yeah it still doing it and now its doing it with the wired connection. I cant use more then one protocol or it will freeze up

---

### Post by Strongman332 on 2009-07-23
put the live cd in to you computer restart check the validity of the disk. then boot the cd check to see if problem persist if not the try a reinstall

---

### Post by cooper77z on 2009-07-23
Maybe try running ubuntu all by itself? Or buy another cheap hardrive 30gigs or so and install ubuntu on it all by itself. Then, when you want to run ubuntu flawlessly, physically remove the dual os hard drive and mannually install the dedicated ubuntu hard drive. I suspect this will solve your problem, though it's kind of extreme :)

Or just install 2 or more hard drives and instruct your bios which one to boot from? Or boot from sd card?

---

### Post by mancrow on 2009-07-23
Why would i need to do that, that is very extreme and if you cant dual boot why would they offer it. i have reinstalled twice now with the 64 bit and 32 bit version. I have gone back to windows till this problem can be fixed i dotn think buying another hard drive will fix the problem i think that is very extreme.

---

### Post by Strongman332 on 2009-07-23
> **mancrow said:**
> Why would i need to do that, that is very extreme and if you cant dual boot why would they offer it. i have reinstalled twice now with the 64 bit and 32 bit version. I have gone back to windows till this problem can be fixed i dotn think buying another hard drive will fix the problem i think that is very extreme.

i dont think this is hard drive related your wireless may not be fully suported yet

---

### Post by mancrow on 2009-07-23
is there a way that i can install some other drives, i just wish that it would get fixed i am sick of windows and would like to get ubuntu working 100%

---

### Post by mancrow on 2009-07-23
> **Strongman332 said:**
> put the live cd in to you computer restart check the validity of the disk. then boot the cd check to see if problem persist if not the try a reinstall

I have checked the hdd and the live cd and there is no problems with those.

---

### Post by cooper77z on 2009-07-23
mancrow said, "Why would i need to do that, that is very extreme and if you cant dual boot why would they offer it."

I know it's extreme. It's fun taking things apart and putting them back together again. It is really easy to remove a hard drive from a laptop. The reason I thought your dropping issue was related to the dual boot hard drive is because I was guessing that windows was trying to control the wifi simultaneously with ubuntu, thus causing droppage. It was just a guess. Small hard drives are real cheap and you could even use it to back up your really important documents.

---

### Post by mancrow on 2009-07-27
> **cooper77z said:**
> mancrow said, "Why would i need to do that, that is very extreme and if you cant dual boot why would they offer it."

I know it's extreme. It's fun taking things apart and putting them back together again. It is really easy to remove a hard drive from a laptop. The reason I thought your dropping issue was related to the dual boot hard drive is because I was guessing that windows was trying to control the wifi simultaneously with ubuntu, thus causing droppage. It was just a guess. Small hard drives are real cheap and you could even use it to back up your really important documents.

They are cheap its getting the stupid adapter from dell to get the hdd to work i have the drive but i am having trouble getting the adapter from them, they are being assholes and want me to use there upgrade depot.

---

### Post by cooper77z on 2009-07-27
That is none too good mancrow. I can't say I doing too much better at the moment everything on my screen is pink and blue with rainbows.:confused:

But I think ubuntu and intel should be able to do a full format on one of your drives pretty easily. :)

---

### Post by mancrow on 2009-08-30
Okie so i reformatted and now i jsut have ubuntu 9.04 on my laptop and there still is the problem with wireless dropping am not dual booting. So just wondering if anyone has any suggestion to what this can be cause am on my last legs with this. I am going to go back to 8 or something where it worked.

---

### Post by P4man on 2009-08-30
2 pages of posts about harddisks (??), and no one even bothered to check or ask exactly what kind of wifi card you have mancrow? 

Please open a terminal and type:

```
lspci 
```

and

```
lsusb
```

(should it be a usb stick.
Also tell me what (if any) sort of wireless security you are using. WEP, WPA/WPA2 ?

---

### Post by mancrow on 2009-08-30
lspci-

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

lsusb-

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



Am running WPA 2 personal 


thanks for the reply hopefully i can get it to work i didnt think it was anything with the hard drives cause that didnt seem right and now i got proof that it isnt.

am going to work right now so wont answer till later tonight but i will do anything to get this fixed cuase i dont like windows.

---

### Post by P4man on 2009-08-30
A broadcom, I should have guessed :s
Not that it will help you, but just so you know.. broadcom drivers have been build by reverse engineering windows driver. Broadcom refuses to disclose the stuff needed to build good linux drivers, and they are not building anything themselves, save for 2 or 3 products. If you get the chance, vote with your wallet and steer clear of their products as much as you can.

Anyway, I assume you are using the native drivers, and not the windows drivers using ndiswrapper ? Have you tried ndiswrapper?

Also, have you tried disabling WPA? I know it kinda sucks to have an open connection, but if it would cure your problem, (and I think it might) and no other solution is found, you could secure your wifi with mac address filtering later.

---

### Post by uylug on 2009-08-30
> **mancrow said:**
> I installed the new ubuntu 9.04 on my laptop and when am using the wireless card it drops the connection. it will still be connected but the internet wont work. The wireless works fine in windows and older versions of ubuntu. The internet will work but it will fade in and out all the time and i have to use a hard line to use the internet without it dropping every 2 minutes.

any help would be great.

Its a dell inspiron 1720 with a dell mini card wifi G card

thanks.

```
sudo iwconfig wlan0 retry 9999999
```

---

### Post by mancrow on 2009-08-31
> **uylug said:**
> ```
sudo iwconfig wlan0 retry 9999999
```



there that and this is what happened

```
 sudo iwconfig wlan0 retry 9999999
Error for wireless request "Set Retry Limit" (8B28) :
    SET failed on device wlan0 ; No such device.
```

---

### Post by P4man on 2009-08-31
you have to replace "wlan0" with whatever linux calls your wireless interface. If its not wlan0 then find out by typing

```
ifconfig
```

(post the result of that while you're at it).

And dont forget to reply to my questions above :)

---

### Post by mancrow on 2009-08-31
> **P4man said:**
> you have to replace "wlan0" with whatever linux calls your wireless interface. If its not wlan0 then find out by typing

```
ifconfig
```

(post the result of that while you're at it).

And dont forget to reply to my questions above :)



Okay sorry for not answering your questions. I have installed the ndiswrapper driver and am currently testing it, they seem to be okay for now no drops. but am keeping my finger crossed and hoping that it stays that way. As for going to an open connection there is no chance of that as we have 6 computers on the wifi and its not my network and i cant just change the settings like that i wish that i could but i cant. 

Thanks for the reply's i really appericate the help. I hoping that all stays okay for now i will report after a bit more of testing.

thanks again.

Edit

Forgot the results i put the command in and i got an error saying limit to high and i adjusted it and the max that i could go was 99 so its set at that.

---

### Post by mancrow on 2009-09-02
Update-
Seems to be a bit more stable still some problems with the wpa 2 networks but am working on getting that changed. 

thanks for all the help i know there isnt much more to do maybe get a usb stick or a new wifi card. ill have to look into it.

---

