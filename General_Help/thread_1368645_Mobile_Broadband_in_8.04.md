---
title: "Mobile Broadband in 8.04"
date: 2009-12-30
forum: General Help
---

### Post by Pesky_Programmer on 2009-12-30
The first Ubuntu OS I used was 9.04 which worked great, but then I upgraded to Karmic... which was a big mistake.The update rendered my desktop unusable and I had to do a fresh install of Ubuntu 9.10. 
Even then the upgrade proved to be less stable then my Windows XP install. Gnome and the windows manager would hang up, my sound would not work, and Blender seamed to run slower then it did on 9.04. Worse my nm-applet icon mysteriously vanished (I eventually got it back but thats another story).
 
So I figured my best option was to downgrade to 8.04. However I can not connect my mobile broadband now(I was able to with the other two version of Ubuntu). There is no icon for the nm-applet program. I even ran a search for the program and could not find it. So using Windows XP I viewed the online docs and noticed that there is no section for connecting a mobile broadband device in 8.04. Except there is one for the newer Ubuntu releases. 
 
Does 8.04 not support Mobile Broadband usb modems?
Does 8.04 not have nm-applet if so how do I connect to a network?

---

### Post by Pesky_Programmer on 2009-12-31
Could some one please help me. My Mobile Broadband device is my only source of internet and I would like to get Ubuntu up to date so I can actually get stuff done with out using Windows XP.
 
Thanks for reading.

---

### Post by Pesky_Programmer on 2010-01-01
Sudo lsusb will not display my novatel wireless card. 
Is there anyway to manually get my card to be detected?

---

### Post by GeorgeVita on 2010-01-01
Hi **Pesky_Programmer**, happy new year!

What type of modem do you have? Give exact model (look at its label).

Try to determine vendorID : productID from **lsusb** using any Ubuntu version (state what version you tried), using the following procedure:
- boot without the modem **wait** for the system to fully load
- open a terminal window and try **lsusb**
- attach modem, **wait** 30 seconds, retry **lsusb**
- compare two outputs to find the 'new line' that must be your modem
- try **dmesg** and check if last 15 lines contain info about 'modem' or 'option driver' etc

Post here above info to follow up.

Regards,
George

---

### Post by Pesky_Programmer on 2010-01-01
>  
Hi **Pesky_Programmer**, happy new year!


 
Happy new year to you too.:)
 
As I said before I tried lsusb and it will not display my modem. However I will try it once more to rule it out, at the moment I am in Windows XP so I will have to reboot to do this.
 
This is not the first time that I have had problems with connecting to the internet in Ubuntu, as this is my third version of Ubuntu I have installed to my laptop. Here is the post from when I had Karmic installed.
 
[http://ubuntuforums.org/showthread.php?t=1329703](http://ubuntuforums.org/showthread.php?t=1329703)
 
After this experience I discovered that I must eject the ROM part of my internet card before ubuntu will detect it as an interenet connection. After doing so I can connect to the internet using the nm-applet icon located in the upper right corner of the screen.
 
However Ubuntu 8.04 will not let me eject the ROM part of my internet card nor is there a nm-applet icon on my screen. I would assume that Ubuntu would come standard with nm-applet, even going as far back as 8.04, but I have been wrong before. 
 
I have looked into methods that explain using a dialer program to connect with my internet card. However I would prefer, if possible, to have Ubuntu detect my wireless card automatically as it did in the past with Jaunty and Karmic.
 
So my question is that is 8.04 supposed to come with the same nm-applet icon/program that was present in the later releases or not?
 
If it did not then is there any way for me to download this program and install it on my 8.04 partition or would it simply not be compatible with the older Ubuntu relsase?
 
Also there is a notification area present on my top panel however it is empty.
 
Again thanks for helping and taking time to read my post.

---

### Post by GeorgeVita on 2010-01-01
> **Pesky_Programmer said:**
> Karmic: After this experience I discovered that I must eject the ROM part of my internet card before ubuntu will detect it as an interenet connection. After doing so I can connect to the internet using the nm-applet icon located in the upper right corner of the screen.
This is the 'normal way' with a possible addition of an 'automatic eject' adding a udev rule, read: [http://ubuntuforums.org/showthread.php?t=1368923](http://ubuntuforums.org/showthread.php?t=1368923)

Although I have not used Ubuntu-Studio, 8.04 has **wvdial** pre-installed. You must define if the communication ports are created: ```
ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
``` but at first the system must 'see' the modem as a USB peripheral.

Do the test following carefully my procedure and post results.

Also post exact model of your modem looking on the sticker label.

Regards,
George

---

### Post by Pesky_Programmer on 2010-01-01
Output of lsusb without the novatel modem inserted 
 
>  
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000 

 
output of lsusb with novatel modem inserted
 
>  
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 005: ID 1410:5030 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000 

 
I am confused as to why my computer will only show 3 of my 4 usb ports without the modem. 
Then with the modem inserted it displays bus 002 twice and says nothing about my modem. I find this odd as the last installs of Ubuntu would always display my modem when it was inserted.
I have tried multiple usb ports on my computer and gotten similar results.
 
My modem is a Novatel wireless USB760 3g modem. Also when ever i try to eject the ROM part of my drive it says it cant because there is no media to be ejected or mounted.
 
I have to boot back into ubuntu to try your above advise I will let you know how it turns out when I am done. Thanks :)

---

### Post by alexfish on 2010-01-01
> **Pesky_Programmer said:**
> The first Ubuntu OS I used was 9.04 which worked great, but then I upgraded to Karmic... which was a big mistake.The update rendered my desktop unusable and I had to do a fresh install of Ubuntu 9.10. 
Even then the upgrade proved to be less stable then my Windows XP install. Gnome and the windows manager would hang up, my sound would not work, and Blender seamed to run slower then it did on 9.04. Worse my nm-applet icon mysteriously vanished (I eventually got it back but thats another story).
 
So I figured my best option was to downgrade to 8.04. However I can not connect my mobile broadband now(I was able to with the other two version of Ubuntu). There is no icon for the nm-applet program. I even ran a search for the program and could not find it. So using Windows XP I viewed the online docs and noticed that there is no section for connecting a mobile broadband device in 8.04. Except there is one for the newer Ubuntu releases. 
 
Does 8.04 not support Mobile Broadband usb modems?
Does 8.04 not have nm-applet if so how do I connect to a network?

Hi

you will have to install usb modeswitch

Add the following to your **/etc/apt/sources.list** file

[INDENT]deb [http://ppa.launchpad.net/wader/ppa/ubuntu](http://ppa.launchpad.net/wader/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/wader/ppa/ubuntu](http://ppa.launchpad.net/wader/ppa/ubuntu) hardy main

From The Terminal

CODE:

[/INDENT]sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5E5F772E
 

 sudo apt-get update && sudo apt-get install usb-modeswitch


 lsusb 


hopefully you should see the device

follow the usb modeswitch guide here

[Ubuntu 9.10 mobile broadband can't connect]("http://ubuntuforums.org/showthread.php?t=1331660") 			([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1331660") [2]("http://ubuntuforums.org/showthread.php?t=1331660&page=2"))


Details on How to connect here

[SIZE=4][http://]("http://ubuntu/")[Linux On The Move]("http://ubuntuforums.org/showthread.php?p=8530340#post8530340")[/SIZE]

---

### Post by GeorgeVita on 2010-01-01
Hi again, I think the 'closer' description of a possible solution is:
[http://ubuntuforums.org/showpost.php?p=6442256&postcount=2](http://ubuntuforums.org/showpost.php?p=6442256&postcount=2)

As this is for Ubuntu 8.10, we are not sure that previous kernels will act in the same way. Main idea is that **1410:5030** refers to the internal virtual cd-rom, changing to **1410:6000** after ejecting it. User **Databit** shows how to do it 'automatically'.

You can see if any 'cd-rom' was created from **dmesg**. My procedure is:
- Boot without modem, **wait** for the system to load
- open a terminal window and try: **sudo dmesg -c**
>>> this will show all system activity till then and will 'clear' this log. Next simple **dmesg** will show 'new' activity only (easier to see what is happening).
- attach modem, **wait** 30 seconds
- from terminal: **dmesg**
- copy all output from THE LAST **dmesg** (not from the previous 'sudo dmesg -c') and post it here.
>>> We need to see any cd-rom created as **sr0**, sr1, ...
- If so you can try to eject it: **sudo eject sr0**
- **wait** 10 seconds
- check **dmesg** and **lsusb** for the new **1410:5030**

Regards,
George

P.S. Hi **alexfish**!

---

### Post by alexfish on 2010-01-01
> **GeorgeVita said:**
> Hi again, I think the 'closer' description of a possible solution is:
[http://ubuntuforums.org/showpost.php?p=6442256&postcount=2](http://ubuntuforums.org/showpost.php?p=6442256&postcount=2)

As this is for Ubuntu 8.10, we are not sure that previous kernels will act in the same way. Main idea is that **1410:5030** refers to the internal virtual cd-rom, changing to **1410:6000** after ejecting it. User **Databit** shows how to do it 'automatically'.

You can see if any 'cd-rom' was created from **dmesg**. My procedure is:
- Boot without modem, **wait** for the system to load
- open a terminal window and try: **sudo dmesg -c**
>>> this will show all system activity till then and will 'clear' this log. Next simple **dmesg** will show 'new' activity only (easier to see what is happening).
- attach modem, **wait** 30 seconds
- from terminal: **dmesg**
- copy all output from THE LAST **dmesg** (not from the previous 'sudo dmesg -c') and post it here.
>>> We need to see any cd-rom created as **sr0**, sr1, ...
- If so you can try to eject it: **sudo eject sr0**
- **wait** 10 seconds
- check **dmesg** and **lsusb** for the new **1410:5030**

Regards,
George

P.S. Hi **alexfish**!

Hi  There again GeorgeVita



it can be done manually

with these commands  

-v : vendor id (prefixed by 0x)
-p : product id (prefixed by 0x)
-d : detach storage driver (value=1)
-H : Huawei Mode (value=1)

So we first execute:[INDENT]$ sudo usb_modeswitch -v 0x"Vendorid" -p 0x"Productid" -d 1[/INDENT]This will detach the storage driver:  Sample

And then :[INDENT]$ sudo usb_modeswitch -v 0x12d1 -p 0x140b -H 1[/INDENT]This will enable the usb modem mode

Now run[INDENT]$ dmesg[/INDENT]Hope it works  / once the mode switch is installed

Regards

 alexfish

---

### Post by Pesky_Programmer on 2010-01-01
GerorgeVita: I followed the other post you gave me the link for and did exactly as it said. I no longer have the cd ROM displayed as a device for my computer. Now it only shows up as a usb drive. I assume this is the empty memory slot on my wireless card which has never stoped me from connecting to the internet in the past so I will ignore it.

Here is the output for dsmeg:

> [   87.051790] usb 2-2: new full speed USB device using ohci_hcd and address 3
[   87.108358] usb 2-2: configuration #1 chosen from 1 choice
[   87.120890] scsi4 : SCSI emulation for USB Mass Storage devices
[   87.121722] usb-storage: device found at 3
[   87.121827] usb-storage: waiting for device to settle before scanning
[   87.125801] scsi5 : SCSI emulation for USB Mass Storage devices
[   87.128199] usb-storage: device found at 3
[   87.128296] usb-storage: waiting for device to settle before scanning
[   89.514567] usb-storage: device scan complete
[   89.516401] scsi 4:0:0:0: CD-ROM            Novatel  Mass Storage     1.00 PQ: 0 ANSI: 2
[   89.525183] usb-storage: device scan complete
[   89.527152] scsi 5:0:0:0: Direct-Access     Novatel  MMC Storage      2.31 PQ: 0 ANSI: 2
[   89.536357] sr1: scsi-1 drive
[   89.536391] sr 4:0:0:0: Attached scsi CD-ROM sr1
[   89.536415] sr 4:0:0:0: Attached scsi generic sg2 type 5
[   89.539469] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   89.539501] sd 5:0:0:0: Attached scsi generic sg3 type 0
[   89.725238] usb 2-2: USB disconnect, address 3
[   90.965584] usb 2-2: new full speed USB device using ohci_hcd and address 4
[   91.101599] usb 2-2: configuration #1 chosen from 1 choice
[   91.112875] scsi6 : SCSI emulation for USB Mass Storage devices
[   91.113864] usb-storage: device found at 4
[   91.113971] usb-storage: waiting for device to settle before scanning
[   93.505893] usb-storage: device scan complete
[   93.507728] scsi 6:0:0:0: Direct-Access     Novatel  MMC Storage      2.31 PQ: 0 ANSI: 2
[   93.511443] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   93.511472] sd 6:0:0:0: Attached scsi generic sg2 type 0


This is after I have rebooted without my modem inserted the using **sudo dmesg -c **cleared the system log. I then inserted the modem and waited 30 seconds and ran dmesg.

I then ran lsusb and here is what it said

> Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 1410:6000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Looks similar to before, my modem is still not showing up :confused:.

Have not tired alexfish's advise yet but don't I need to be online to use those commands?

Thanks for the help so far :).

On a side note: I found my Jaunty disk earlier today and have installed it. So I have a triple boot Windows XP, Jaunty, and 8.04. However I would still like to get 8.04 to work since it is still being supported with updates.

---

### Post by alexfish on 2010-01-01
> **Pesky_Programmer said:**
> GerorgeVita: I followed the other post you gave me the link for and did exactly as it said. I no longer have the cd ROM displayed as a device for my computer. Now it only shows up as a usb drive. I assume this is the empty memory slot on my wireless card which has never stoped me from connecting to the internet in the past so I will ignore it.

Here is the output for dsmeg:



This is after I have rebooted without my modem inserted the using **sudo dmesg -c **cleared the system log. I then inserted the modem and waited 30 seconds and ran dmesg.

I then ran lsusb and here is what it said



Looks similar to before, my modem is still not showing up :confused:.

Have not tired alexfish's advise yet but don't I need to be online to use those commands?

Thanks for the help so far :).

On a side note: I found my Jaunty disk earlier today and have installed it. So I have a triple boot Windows XP, Jaunty, and 8.04. However I would still like to get 8.04 to work since it is still being supported with updates.


Hi

your on line now with another computer



  follow posts on how to get updates on usb memory sticks

   there are some recent posts about this  here

[http://ubuntuforums.org/showthread.php?t=1368648](http://ubuntuforums.org/showthread.php?t=1368648)

---

### Post by Pesky_Programmer on 2010-01-01
alexfish: thanks for the link. I will experiment and see if I can get Jaunty to download the updates for my other Ubuntu, and will post the results when I am done.

At the vary least I am learning more about Linux whether I get it to work or not thanks for the help.

> 
your on line now with another computer
Actually I am doing all of this off of one laptop with a 120 GB hard drive, its a wonder it has not exploded yet :P.

---

### Post by alexfish on 2010-01-01
Hi 

Just Done and

I can Confirm This 

download usb modeswitch here form internet access
[http://packages.debian.org/squeeze/usb-modeswitch](http://packages.debian.org/squeeze/usb-modeswitch)

save to usb stick  and run from the ubuntu 8.04 reboot and you will see it with the "lsusb" command

follow the guide mentioned on previous post on how to get connected 

good luck

---

### Post by GeorgeVita on 2010-01-02
> **Pesky_Programmer said:**
> ...However I would still like to get 8.04 to work since it is still being supported with updates.
Except mobile broadband as newer kernels support better 3g modems.

According to [http://ubuntuforums.org/showpost.php?p=6442256&postcount=2](http://ubuntuforums.org/showpost.php?p=6442256&postcount=2)
(lsusb shows the modem 1410:6000 ) next step is to check/edit HAL parameters file:```
gksudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
``` search (**ctrl+F**) to find '**0x1410**', I found the following paragraph into Ubuntu 9.04 file: ```
      <!-- Novatel -->
      <match key="@info.parent:usb.vendor_id" int="0x1410">
        <!-- Merlin XS620/S640,S620,EX720,S720,EV620 CDMA/EV-DO,ES620/Merlin ES720/Ovation U720,ES620 SM Bus,U727 -->
        <match key="@info.parent:usb.product_id" int_outof="0x1100;0x1110;0x1410;0x1120;0x1130;0x2100;0x2110;0x2130;0x4100;0x5010">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">IS-707-A</append>
          </match>
        </match>
        <!-- U730,U740,EU870,XU870 HSDPA/3G,EU740,EU870D,MC950 -->
        <match key="@info.parent:usb.product_id" int_outof="0x1400;0x1410;0x1420;0x1430;0x2410;0x2420;0x4400">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>
      </match>

```
**Important:** If your modem is a CDMA you must use 'IS-707-A' part, otherwise for a HSDPA modem you need the **GSM-07.0x** part.

Edit appropriate line to include **0x6000**  ('...info.parent:usb.product_id...) and save that file.
Below are two options:

**CDMA** (3rd line after 'Novatel') ```
        <match key="@info.parent:usb.product_id" int_outof="0x1100;0x1110;0x1410;0x1120;0x1130;0x2100;0x2110;0x2130;0x4100;0x5010;0x6000">

```

**GSM HSDPA** (9th line after Novatel)
```
        <match key="@info.parent:usb.product_id" int_outof="0x1400;0x1410;0x1420;0x1430;0x2410;0x2420;0x4400;0x6000">
 
```

Regards,
George

P.S. alternative way (as **Alexfish** tested) will show the modem using usb_modeswitch but I think you have to 'trim' also .fdi file (for 8.04).

---

### Post by Pesky_Programmer on 2010-01-02
**Alexfish: **I am trying the usb switcher now will post back when im done.

---

