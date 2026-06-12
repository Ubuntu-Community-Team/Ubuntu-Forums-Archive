---
title: "USB WiFi - D-Link WUA-1340 - SOL maybe?"
date: 2006-03-18
forum: General Help
---

### Post by enfact on 2006-03-18
I just  bought this card, D-Link WUA-1340, i am guessing it is a rt2500 card but i cant find a bit on it on the ndiswrapper wiki pages or anything. Its a newer card, i really hope im not SOL. The driver that comes with it on CD  dosent have any infs on it, all exe's that extract the drivers and windows says the only driver files it uses are Dr71WU.sys... The file is signed "Ralink 801.11 USB Wireless Adapter Driver" version 1.0.1.0. I installed the sys file with ndiswrapper and it was "invalid"

Here's my outputs...

USB  stuff from  lshw...

irq:10
        *-usb:0
             description: USB Controller
             product: 82801CA/CAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1800-181f irq:10
           *-usbhost
                product: Intel Corporation 82801CA/CAM USB (Hub #1)
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: 802.11 bg WLAN
                   vendor: Ralink
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.01
                   capabilities: usb-2.00
                   configuration: maxpower=300mA speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801CA/CAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:5
           *-usbhost
                product: Intel Corporation 82801CA/CAM USB (Hub #2)
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s

---------------------------------------------------------

lspci:

0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 05)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 05)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
0000:02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:02:04.0 CardBus bridge: O2 Micro, Inc. OZ6912 Cardbus Controller


---------------------------------------------------------

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:08:74:3C:57:59
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe3c:5759/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1693046 (1.6 MiB)  TX bytes:227161 (221.8 KiB)
          Interrupt:10 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1111 (1.0 KiB)  TX bytes:1111 (1.0 KiB)

---------------------------------------------------------

iwconfig:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---------------------------------------------------------

lsusb:

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 07d1:3c04 D-Link System
Bus 001 Device 001: ID 0000:0000


-------------------------------------------------------

There are a couple different places to find info about getting the ralink rt2500 set up but they arent great.  Please if you are sure thats what i need and that this card uses that chipset, post the link that worked for you. Im running breezy.

Thanks!

---

### Post by jz_element on 2006-06-22
Hi any luck since that. I found there is driver for this D-Link WUA-1340 from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List). Than search WUA on that page you will find it, but I didn't make it work either. Anyone know how to make it work?

---

### Post by saveryquinn on 2006-09-14
Hello!

Having stumbled blindly for three days with USB wifi 'cards' that didn't work with Dapper (a Belkin, a US Robotics too) I almost ran out of excuses to tell store clerks why I was returning a working USB wifi 'card' (didn't want to hear one more clerk tell me "Well of course it doesn't work.  It isn't made for Linux).  Finally bought the D-Link WUA-1340 Wireless G USB 2.0 Adapter.  

Works through ndiswrapper like an ugly black charm (well, when your laptop is an Inspirion 6400 black just doesn't go with it).  

How'd it work?  WARNING: Relative Linux newbie offering advice here.  Use caution.  There may be and probably are a half-dozen simpler ways of doing this.

Pre: Running Ubuntu Dapper (Gnome) on a Dell Inspirion 6400 with the latest version of ndiswrapper and wine from the Ubuntu repositories.

1. Put the D-Link resource CD in the drive.  Plug in the adapter.  

2. Go to the file "Drivers"

3. There sits a file "setup.exe"

4. In the shell type: wine setup.exe or in Nautilus 'right-click' the icon and either "Open with Wine" or "Open With Other Application."  In the case of the latter, when the new 'select your app' window opens, click "Use a Custom Command" and enter "wine" in that command line.

5. The D-Link setup wizard should appear.  Follow all the steps just like you were in good ol Windows.

6. Once the installation is complete DON'T EXPECT your usb device to be working just yet (even though the setup wizard suggests it might be).

7. In Nautilus open your "Home" folder.  Crtl-H to show your hidden files.  Scroll down and open folder ".wine." 

8. Now open the folder "drive_c"

9. Now open the folder "program files"

10. In that file there should be (if Wine and the D-Link wizard were successful) a folder named "Drivers"  You can make sure this is the correct folder by opening it.  Inside should be a number of files including that oh-so-prized Dr71WU.inf file!

11. Copy this whole "Drivers" folder to your home directory or wherever you'd like to have it for ndiswrapper's needs.

12. Once copied, go back to the command line.

13. Run: ndiswrapper -l

14. Run: sudo ndiswrapper -i /home/yourname/yourdirectory/dr71wu.inf
 (note here: on my laptop the inf file, when copied to my home folder, transformed from Dr71WU.inf to dr71wu.inf)

15. Run: ndiswrapper -l   to see if the driver loaded.  If everything worked you should see that both the driver and the hardware are present.

16. Run: sudo modprobe ndiswrapper

That's about it. 

My adapter wasn't running until I rebooted my computer.  That's an old Windows habit.

If you run into trouble during the installation, check resource pages for wine and ndiswrapper running under Ubuntu.

Good luck!

---

### Post by jcanady on 2006-09-23
Have you guys had any problems with setting the mode?  

I have used Fedora for years, and I had a wireless PCMCIA card.  Then, it slid forward in the card and broke the card and slot.  So, now I purchased a D-Link WUA-1340 at Office Max.  

I'm not having much luck. I got ndiswrapper to detect it (and Linux/Fedora), but it won't go out of Ad-Hoc mode (easily).  I can use the NetworkManager (part of GNOME), and it will finally work.  But, it takes a while sometimes.  Even then, it gives me a dynamic IP (I use a static IP), and it gives me the wrong DNS that I normally use.  

I would really like to have my wireless back!  Thanks so much.

Best Regards,

Jason

---

### Post by Robert Citek on 2006-10-31
> **saveryquinn said:**
> Works through ndiswrapper like an ugly black charm (well, when your laptop is an Inspirion 6400 black just doesn't go with it).
...
Good luck!
Thanks for your notes.  They worked really well for me.  Below are my notes which are based on yours.  This was done on a Dell Latitude D610 running Ubuntu 6.06 LTS.

Installing the drivers from the CD using the Terminal application (Applications > Accessories > Terminal).

```
[FONT="Courier New"]
sudo apt-get update
sudo apt-get install wine ndiswrapper-utils          # install wine and ndiswrapper
wine /media/cdrom/Drivers/setup.exe                  # unpackage drivers
:                                                    # insert WUA-1340 into the USB port when instructed
ndiswrapper -l                                       # check nsdiswrapper
sudo ndiswrapper -i \
  ~/.wine/drive_c/Program\ Files/Drivers/Dr71WU.inf  # insert driver
ndiswrapper -l                                       # check nsdiswrapper
sudo modprobe ndiswrapper                            # load ndis module
lsmod  | grep ndis                                   # check list of loaded modules
dmesg | tail                                         # determine new device name
ifconfig wlan0                                       # check interface
sudo ndiswrapper -m                                  # add config to /etc/modprobe.d
cat /etc/modprobe.d/ndiswrapper                      # display module entry
[/FONT]
```

Connecting the WUA-1340 USB wifi adapter

```
[FONT="Courier New"]
sudo modprobe ndiswrapper      # load ndis
:                              # insert WUA-1340 into USB port
dmesg | tail                   # determine new device name
ifconfig wlan0                 # check interface
iwconfig wlan0                 # check wireless settings
iwlist wlan0 scan              # scan for WAPs
sudo iwconfig wlan0 \
 essid "Free/Libre/OpenSource" # attach to WAP
iwconfig wlan0                 # check wireless settings
sudo dhclient3 wlan0           # request IP address
ifconfig wlan0                 # check interface
ping -c 4 cwelug.org           # check networking
[/FONT]
```

Disconnecting the WUA-1340 USB wifi adapter

```
[FONT="Courier New"]
sudo dhclient3 -r wlan0        # release IP address
ifconfig wlan0                 # check interface
:                              # remove WUA-1340 from USB port
ifconfig wlan0                 # check interface
iwconfig wlan0                 # check wireless settings
[/FONT]
```

Regards,
- Robert

---

### Post by superyounan1 on 2007-02-28
> **saveryquinn said:**
> Hello!

Having stumbled blindly for three days with USB wifi 'cards' that didn't work with Dapper (a Belkin, a US Robotics too) I almost ran out of excuses to tell store clerks why I was returning a working USB wifi 'card' (didn't want to hear one more clerk tell me "Well of course it doesn't work.  It isn't made for Linux).  Finally bought the D-Link WUA-1340 Wireless G USB 2.0 Adapter.  

Works through ndiswrapper like an ugly black charm (well, when your laptop is an Inspirion 6400 black just doesn't go with it).  

How'd it work?  WARNING: Relative Linux newbie offering advice here.  Use caution.  There may be and probably are a half-dozen simpler ways of doing this.

Pre: Running Ubuntu Dapper (Gnome) on a Dell Inspirion 6400 with the latest version of ndiswrapper and wine from the Ubuntu repositories.

1. Put the D-Link resource CD in the drive.  Plug in the adapter.  

2. Go to the file "Drivers"

3. There sits a file "setup.exe"

4. In the shell type: wine setup.exe or in Nautilus 'right-click' the icon and either "Open with Wine" or "Open With Other Application."  In the case of the latter, when the new 'select your app' window opens, click "Use a Custom Command" and enter "wine" in that command line.

5. The D-Link setup wizard should appear.  Follow all the steps just like you were in good ol Windows.

6. Once the installation is complete DON'T EXPECT your usb device to be working just yet (even though the setup wizard suggests it might be).

7. In Nautilus open your "Home" folder.  Crtl-H to show your hidden files.  Scroll down and open folder ".wine." 

8. Now open the folder "drive_c"

9. Now open the folder "program files"

10. In that file there should be (if Wine and the D-Link wizard were successful) a folder named "Drivers"  You can make sure this is the correct folder by opening it.  Inside should be a number of files including that oh-so-prized Dr71WU.inf file!

11. Copy this whole "Drivers" folder to your home directory or wherever you'd like to have it for ndiswrapper's needs.

12. Once copied, go back to the command line.

13. Run: ndiswrapper -l

14. Run: sudo ndiswrapper -i /home/yourname/yourdirectory/dr71wu.inf
 (note here: on my laptop the inf file, when copied to my home folder, transformed from Dr71WU.inf to dr71wu.inf)

15. Run: ndiswrapper -l   to see if the driver loaded.  If everything worked you should see that both the driver and the hardware are present.

16. Run: sudo modprobe ndiswrapper

That's about it. 

My adapter wasn't running until I rebooted my computer.  That's an old Windows habit.

If you run into trouble during the installation, check resource pages for wine and ndiswrapper running under Ubuntu.

Good luck!

What version of WINE are you using? I have the latest 0.9.3.1 and  I cant get past step 5 becaue I keep getting errors from WINE right at the point where the installer is about to start copying files and then fails! GRRR, here are the errors the terminal spat out:

```
err:msi:ACTION_CallDllFunction failed to find action {0163c280-0000-0000-0000-000001000000}
err:msi:ITERATE_Actions Execution halted, action L"ISStartup" returned 1603

```

And I couldn't find any useful info on how to fix this. So instead I tried looking up the native railink drivers and building them, but that didn't work, then I found a tutorial that said you had ot modify one of the header files to get it to work with D-Link, followed all instructions to the letter and STILL doesn't. 

Then I thought 'just install the drivers in windows and find the .sys and .inf files, copy them over!', but the .INF file is no where to be found, only the .SYS. 

Will someone just give me a sure fire way to get this done? should i downgrade WINE to older versions until one of them can install the setup, then use ndiswrapper?

---

### Post by superyounan1 on 2007-03-03
Hey guys, I finally got my card up and running, and I didn't do it using ndiswrapper, rather i went directly to the ralink chipset native drivers and followed the guide written by my personal hero "TripleWithCheese" on this page,

[http://ubuntuforums.org/showthread.php?t=270756&highlight=wua-1340+ralink](http://ubuntuforums.org/showthread.php?t=270756&highlight=wua-1340+ralink)

If you can get it working with ndis, more power to you, but if you're also having the problem where wine cant run the dlink installer, then its probably because you're using wine version 9.31, which for me, crashed every time right at the good part of the installation - try instead version 9.30 which you can find by clicking around on their site.

---

### Post by helland on 2007-08-07
Please help me. Done this

1. Put the D-Link resource CD in the drive. Plug in the adapter. 

2. Go to the file "Drivers"

3. There sits a file "setup.exe"

4. In the shell type: wine setup.exe or in Nautilus 'right-click' the icon and either "Open with Wine" or "Open With Other Application." In the case of the latter, when the new 'select your app' window opens, click "Use a Custom Command" and enter "wine" in that command line.

5. The D-Link setup wizard should appear. Follow all the steps just like you were in good ol Windows.

6. Once the installation is complete DON'T EXPECT your usb device to be working just yet (even though the setup wizard suggests it might be).

7. In Nautilus open your "Home" folder. Crtl-H to show your hidden files. Scroll down and open folder ".wine." 

8. Now open the folder "drive_c"

9. Now open the folder "program files"

10. In that file there should be (if Wine and the D-Link wizard were successful) a folder named "Drivers" You can make sure this is the correct folder by opening it. Inside should be a number of files including that oh-so-prized Dr71WU.inf file!

11. Copy this whole "Drivers" folder to your home directory or wherever you'd like to have it for ndiswrapper's needs.

12. Once copied, go back to the command line.

13. Run: ndiswrapper -l

14. Run: sudo ndiswrapper -i /home/yourname/yourdirectory/dr71wu.inf
(note here: on my laptop the inf file, when copied to my home folder, transformed from Dr71WU.inf to dr71wu.inf)

15. Run: ndiswrapper -l to see if the driver loaded. If everything worked you should see that both the driver and the hardware are present.

16. Run: sudo modprobe ndiswrapper

That's about it. 

My adapter wasn't running until I rebooted my computer. That's an old Windows habit.

If you run into trouble during the installation, check resource pages for wine and ndiswrapper running under Ubuntu.


But the usb adapter do not work (it shows networks, bu can not connect...Stops on stage config device

---

### Post by helland on 2007-08-08
Do not know why, but it started and worked few mins....Than again!

---

### Post by jakswa on 2007-09-20
I used this wireless network adapter... took me a day and a half of searching, and just about the time i was about to give up (after fiddling for hours with ndiswrapper), I found WICD!

WICD is a network manager, and it takes the place of the "Network-manager" package that comes with ubuntu.

edit:  I'm a noob like you, so don't expect me to know whats up if you run into problems with the way that I did this... (but I would like to know if you did)

I simply:

--uninstalled the Network-manager package  (using System>Administration>synaptic package manager)

--installed the WICD package 
(if you're accessing the internet from a windows computer, just download from sourceforge:  [http://downloads.sourceforge.net/wicd/wicd_1.3.1-all.deb?modtime=1184023948&big_mirror=0](http://downloads.sourceforge.net/wicd/wicd_1.3.1-all.deb?modtime=1184023948&big_mirror=0) )

--ran the WICD package, and it saw my router, and i clicked 'connect' and POOF!  wireless internet!

I'm talking to you about 5 minutes after i got it working (I'm spreading the word.)

edit:  I'm not sure if uninstalling network manager will disconnect your ubuntu system if you are currently accessing the internet from it (through wired connection, and trying to get wireless to work).  So you might want to make sure you have the necessary file (the WICD .deb) downloaded before uninstalling network manager.

---

### Post by Wodentheow on 2007-10-20
Missing .inf

I was following the instructions and also got stuck when I couldn't find the .inf file. I found the answer on another forum (can't remember where):

look in /home/yourname/.wine/drive_c/windows/inf

Where yourname is your profile name and .wine is a hidden folder.

---

### Post by jdix123 on 2008-01-04
Ok, so I've done everything listed with running the installer with WINE, copying the drivers folder, and running ndiswrapper -i dr71wu.inf.

Well, first of all, my .wine/c-drive/program files/d-link/drivers folder never had a dr71wu.inf file as far as I can tell, only a dr71wu.sys file.

But then I found one in a different directory under .wine/c-drive/windows/inf  No big deal, start again.

So I run ndiswrapper -l and I get:

Installed ndis drivers:
dr71wu invalid driver!

If I try to remove it using ndiswrapper -e dr71wu

I get no further output, just another prompt, but running -l once again pops up the same invalid driver.  I can't try to reinstall it (I think I typed it wrong might be why its not working) because it says its already installed, but it doesn't remove it.

---

