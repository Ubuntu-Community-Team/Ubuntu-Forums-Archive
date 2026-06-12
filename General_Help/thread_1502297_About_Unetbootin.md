---
title: "About Unetbootin"
date: 2010-06-05
forum: General Help
---

### Post by satimis on 2010-06-05
Hi folks,

Ubuntu 10.04
Unetbootin – linux version
Window-7.iso

On "Distribution" of Unetbootin drop-list I can't find Windows. However the Windows-7.iso is on Ubuntu. I can't run Unetbootin Windows version here. Is there a solution? TIA

B.R.
satimis

---

### Post by C.S.Cameron on 2010-06-05
Do you want to install windows using UNetbootin? (It does not work), or do you want to use UNetbootin while in Windows?

---

### Post by Barafu Albino Cheetah on 2010-06-05
There is no way to write Windows disk on USB stick. Only UNIX family systems are designed well enough to make such tricks.

---

### Post by satimis on 2010-06-05
Hi folks,

I want to write Windows ISO on USB drive in Linux environment.  There is a trick writing Windows ISO on USB drive but in Windows environment.

How to Install Windows 7 From USB Drive without Windows 7 ISO DVD
[http://www.blogsdna.com/2016/how-to-install-windows-7-from-usb-drive-without-windows-7-iso-dvd.htm](http://www.blogsdna.com/2016/how-to-install-windows-7-from-usb-drive-without-windows-7-iso-dvd.htm)

The package doesn't work on wine.  I tested it.

B.R.
satimis

---

### Post by C.S.Cameron on 2010-06-05
> There is no way to write Windows disk on USB stick. Only UNIX family systems are designed well enough to make such tricks

Not true.

I have got XP running from flash drive using advice from this page:
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

But I don't know how to get a Win 7 iso working from USB as requested in this thread.

---

### Post by satimis on 2010-06-05
> **C.S.Cameron said:**
> Not true.

I have got XP running from flash drive using advice from this page:
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

But I don't know how to get a Win 7 iso working from USB as requested in this thread.

Hi,

Thanks for your advice and thread.  Unfortunately the server doesn't work.  Are there alternative links?  Thanks

B.R.
satimis

---

### Post by C.S.Cameron on 2010-06-06
Dang, the site was down once before but came back up after a few days.
Check it again in a few days.
I'll search my computer to see if I made a copy.

Edit:
Lets see if this works converted into a txt file:

windows_xp-prostick.png 	

The ultimate guide for installing and running Windows XP from a USB stick / HDD drive
bubble.jpg

Find tons of help with installation issues on our Windows XP on USB Forum

    What is this about?

    To keep the introduction short, Microsoft denies that booting Windows off a USB drive works.

    See this page for example. It says:

        Q: Can a USB storage device be the primary (and only) means of storage?
        No. USB-based mass storage devices cannot be the primary hard disk storage solution on a regular system ...

    Or this one from the microsoft newsgroups:

        Windows cannot boot from an USB drive. If your computer supports
        booting from such device, you can load a boot loader to the USB device
        which starts Windows XP from the HDD.

    Anyway, the web is full of those. I was wondering about the same thing, as i did not want to put a Windows partition on my Linux.based work laptop, and thought it was a good idea to run Windows XP off a USB Hard drive that i just plug in when i need it, and boot from it. To put a long story short, this is exactly what i do now, thanks to the fantastic research of the people credited below. However, it took me significant time to figure out all the painful little problems, and i was not fully happy with the current official guide by Dietmar (no pun, he was the first to make ANYthing public). I wanted an easy guide that allows creating a modified version of the Windows XP CD, for painless and transparent installation to as many systems as you want.

    This page is the result of my work. Have fun!

Credits

    ...must go to the people that made this guide possible in the first place. In recent months, a few blokes going by the handles of mkiaer, Dietmar and sisal and a few others from the 911.net forums came up with many good pieces of research on how to enable any NT-based Windows to boot from a USB-drive. Little of this guide would exist without them - in fact the only reason why i write this up is that my particular solution seems to be lower effort than any of the steps i saw before. Many of the steps here are the result of their research.

Version History:

    * v1.0 - 3rd Mar 2006
      rewritten, tested and working against two different drives with my laptop.
    * v0.9 - 29th Feb 2006
      initial version, untested

What works?

    Basically, everything as far as i can see. After completing this tutorial, your Windows XP install should directly boot off your USB-drive, and be fully upgradable, DirectX games will run, all apps i tested work like normal, speed is the same as with a real HDD (you need USB2 though) - so it is in fact a fine solution as far as i can see.

    Host Hardware 	USB hardware 	Successful
    Dell Latitude D820 	WD Pocket Drive 80gb 	Yes
    DFI Infinity Ultra 2
    	Dane Elec 4GB USB Stick
    	Yes
    Asus M2A-VM HDMI
    	Adata PD2 4GB Stick
    	Yes
    HP Compaq 6510b
    	WD 2908A
    	Yes
    Compaq nc6400
    	WD2500BEV
    	Yes
    Compaq nc6400
    	Trekstore i.Beat 2GB
    	No
    Compaq nc6400
    	Hitachi DK23EA-30
    	No
    Compaq nc6220
    	TrackStore DataStation XU
    	Yes
    HP Pavillion dv6700t
    	InfoSafe USB with Toshiba SATA 250GB
    	Yes
    Compaq nc6120
    	Lacie 80gb
    	Yes
    Asus P5LD2-VM
    	Vantec IDE to USB cable + Maxtor 60gb PATA
    	Yes
    Thinkpad T42
    	WD HDD Passport 2
    	Yes
    Acer Aspire 5600
    	Ipod 20g Photo
    	Yes
    Thinkpad T43
    	Generic 80gb USb2 case
    	Yes
    HP Pavillion dv1000
    	Generic USB2 HDD
    	Yes
    Thinkpad R61
    	Generic USB2 / Seagate 120 GB
    	Yes
    Dell Latitude D620
    	PQI i221 USB stick
    	Yes
    Fujitsu Lifebook E8410C
    	Shintaro USB2 + 80GB Samsung
    	Yes
    Dell Inspiron 6400
    	generic USB2 enclosure
    	Yes
    Intel 945 GNT
    	Kingston 4GB SDHC with USB adapter
    	Yes
    HP nx6110
    	Sandisk Cruze 8gb
    	Yes
    HP nx6110
    	OneTouch4 Mini
    	No
    Dell Latitude D620
    	Seagate FreeAgent 500GB
    	Yes
    Acer Aspire 5710G
    	Adata 4GB stick
    	Yes
    ...and LOTS more...
    	
    	

Disclaimer

    This is a hobby project of mine. I will not assume ANY responsibility for the correctness of this guide, nor can I be made liable for any errors, hardware or software problems / loss that are caused by following this guide. Basically, if things screw up, its your own fault. Do not follow the guide if you fear data loss.

Requirements

    * An existing Windows install for carrying out the steps in this tutorial
    * A USB2-compliant Hard disk drive (or a big USB2 stick, see remarks below)
    * An original Windows XP CD (tested only against SP1 so far, but reported to work on other versions)
    * A registered version of WinISO (or any other software that allows direct editing of ISO files)
    * The Microsoft CAB SDK
    * A CD-burning software that can handle ISO files. I like the free burnatonce

How To:

Summary:

We will dump the contents of your original Windows XP CD , extract a few files from the Image using ISO modification software, edit the files, and put the modified versions back on the ISO. The resulting ISO image is burnt back onto a CD media, and can then directly be used to install Windows on your USB drive.

I am also covering a few pitfalls that happened to me, in hope they will save you a bit of time.

 

1) Does your computer support booting from USB?

    Usually, if its an option in your BIOS boot sequence menu, the answer to this is yes. If its not there, look for BIOS updates. If you are not sure, proceed and see what happens ;-)

2) Sorting out the "Bootability" of your USB-Drive

    Connect your USB drive to your computer, directly, without a Hub. Then, shut down your computer, disconnect any other hard disk drives from it, and insert your original Windows XP CD into the drive. Start the installation, and proceed to the section where you are allowed to pick a hard drive. If it goes beyond the partition selection, your drive is already fine for booting Windows XP. If not (seems to be the cases with many of the Freecom USB HDDs for example), you will get an error like "Windows is unable to find your drive, partition, data etc bla". This is usually not a big problem. All you need to do is "properly" format the drive. Reboot into your normal Windows, and get this HP tool , and use it to format your HDD completely. I chose NTFS format, worked fine everytime i tried. After this, my drives are recognized as valid installation devices by the Windows XP installer.
    (In fact, i did not manage to create a USB primary partition with FAT32 that was recognized as being installable)

3) Dumping the original Windows CD into an ISO File

 

    Pretty easy one. Simply open WinISO, and select Actions -> Make ISO from CDROM, and save your CD image.

 

4) Extracting the files we need to work on

 

    After the CD dump is done, close and reopen WinISO. Then, open the ISO file you just created using File -> Open.
    Now, click the I386 folder, and select the following files (Ctrl key to multi-select)

        * TXTSETUP.SIF
        * DOSNET.INF
        * USB.IN_
        * USBPORT.IN_
        * USBSTOR.IN_

    Select Actions -> Extract and put the resulting files into some folder to work on them.

5) Unpacking IN_ files

 

 

    Use the Cab SDK (from the command line) for extracting the contents of the .IN_ files. Each of them contains exactly one .inf file. If you are unsure how to use the Cab SDK, here is an example command line: "cabarc x USBSTOR.IN_" . You should end up with three new files in the folder, called:

        * usb.inf
        * usbport.inf
        * usbstor.inf

    You can now delete the .IN_ files.

6) Editing the files

    This is the main job. i ll also try to explain a bit whats happening. Use a simple Texteditor like Notepad.

    6-A) TXTSETUP.SIF

        This file is loaded on the initial install step by the Windows XP CD installer. In this file, we will change the way Windows treats USB devices during system setup -- the default is to only treat them as input devices during installation -- we will change this to include mass storage driver support (which needs to be loaded into the installer much earlier in order to work).

        First, move the following entries from [InputDevicesSupport.Load] to the [BootBusExtenders.Load] section , as shown here

         

            [BootBusExtenders.Load]
            pci = pci.sys
            acpi = acpi.sys
            isapnp = isapnp.sys
            acpiec = acpiec.sys
            ohci1394 = ohci1394.sys
            usbehci = usbehci.sys
            usbohci = usbohci.sys
            usbuhci = usbuhci.sys
            usbhub = usbhub.sys
            usbstor = usbstor.sys


            [InputDevicesSupport.Load]
            usbehci = usbehci.sys
            usbohci = usbohci.sys
            usbuhci = usbuhci.sys
            usbhub = usbhub.sys
            usbccgp = usbccgp.sys
            hidusb = hidusb.sys
            serial = serial.sys
            serenum = serenum.sys
            usbstor = usbstor.sys

         

        ... now the same for [BootBusExtenders] and [InputDevicesSupport]

         

            [BootBusExtenders]
            pci = "PCI-Bustreiber",files.pci,pci
            acpi = "ACPI Plug & Play-Bustreiber",files.acpi,acpi
            isapnp = "ISA Plug & Play-Bustreiber",files.isapnp,isapnp
            acpiec = "Integrierter ACPI-Controllertreiber",files.none,acpiec
            ohci1394 = "IEEE-1394-Bus-OHCI-konformer Anschlusstreiber",files.ohci1394,ohci1394
            usbehci = "Erweiterter Hostcontroller",files.usbehci,usbehci
            usbohci = "Open Hostcontroller",files.usbohci,usbohci
            usbuhci = "Universeller Hostcontroller",files.usbuhci,usbuhci
            usbhub = "Standard-USB-Hubtreiber",files.usbhub,usbhub
            usbstor = "USB-Speicherklassentreiber",files.usbstor,usbstor


            [InputDevicesSupport]
            usbehci = "Erweiterter Hostcontroller",files.usbehci,usbehci
            usbohci = "Open Hostcontroller",files.usbohci,usbohci
            usbuhci = "Universeller Hostcontroller",files.usbuhci,usbuhci
            usbhub = "Standard-USB-Hubtreiber",files.usbhub,usbhub
            hidusb = "HID-Parser",files.hidusb,hidusb
            serial = "Treiber f&#65533;r seriellen Anschluss",files.none,serial
            serenum = "Enumerator f&#65533;r seriellen Anschluss",files.none,serenum
            usbstor = "USB-Speicherklassentreiber",files.usbstor,usbstor
            usbccgp = "USB Generic Parent Driver",files.usbccgp,usbccgp 

         

        Next, we also have to write several keys into the registry. Convieniently, the txtsetup.sif allows you to specify files that are parsed and instered into the registry at install time. Insert the following in the [HiveInfs.Fresh] section:

            [HiveInfs.Fresh]
            AddReg = hivedef.inf,AddReg
            AddReg = hivesys.inf,AddReg
            AddReg = hivesft.inf,AddReg
            AddReg = hivecls.inf,AddReg
            AddReg = hiveusd.inf,AddReg
            AddReg = dmreg.inf,DM.AddReg
            AddReg = usbboot.inf,usbservices

         

        and also in [SourceDisksFiles]

            [SourceDisksFiles]
            usbboot.inf = 1,,,,,,_x,3,,3
            bootvid.dll = 1,,,,,,3_,2,0,0,,1,2
            kdcom.dll = 1,,,,,,3_,2,0,0,,1,2

        Finally, save and close TXTSETUP.SIF. We are done with it.

    6-B) DOSNET.INF

        Now, open DOSNET.INF , and change the second [Files] section to look like this:

        [Files]
        d1,usbboot.inf
        d1,_default.pif
        d1,12520437.cpx
        d1,12520850.cpx

        ....

    6-C) usb.inf

        Change the bolded lines in the [StandardHub.AddService] and [CommonClassParent.AddService] sections:

        [StandardHub.AddService]
        DisplayName = %StandardHub.SvcDesc%
        ServiceType = 1 ; SERVICE_KERNEL_DRIVER
        StartType = 0 ; SERVICE_DEMAND_START
        ErrorControl = 1 ; SERVICE_ERROR_NORMAL
        ServiceBinary = %12%\usbhub.sys
        LoadOrderGroup = Boot Bus Extender

        [CommonClassParent.AddService]
        DisplayName = %GenericParent.SvcDesc%
        ServiceType = 1 ; SERVICE_KERNEL_DRIVER
        StartType = 0 ; SERVICE_DEMAND_START
        ErrorControl = 1 ; SERVICE_ERROR_NORMAL
        ServiceBinary = %12%\usbccgp.sys
        LoadOrderGroup = Boot Bus Extender

    6-D) usbport.inf

        Change the bolded lines in the [EHCI.AddService], [OHCI.AddService] , [UHCI.AddService] and [ROOTHUB.AddService] sections:

        [EHCI.AddService]
        DisplayName = %EHCIMP.SvcDesc%
        ServiceType = 1 ; SERVICE_KERNEL_DRIVER
        StartType = 0 ; SERVICE_DEMAND_START
        ErrorControl = 1 ; SERVICE_ERROR_NORMAL
        ServiceBinary = %12%\usbehci.sys
        LoadOrderGroup = Boot Bus Extender

        [OHCI.AddService]
        DisplayName = %OHCIMP.SvcDesc%
        ServiceType = 1 ; SERVICE_KERNEL_DRIVER
        StartType = 0 ; SERVICE_DEMAND_START
        ErrorControl = 1 ; SERVICE_ERROR_NORMAL
        ServiceBinary = %12%\usbohci.sys
        LoadOrderGroup = Boot Bus Extender

        [UHCI.AddService]
        DisplayName = %UHCIMP.SvcDesc%
        ServiceType = 1 ; SERVICE_KERNEL_DRIVER
        StartType = 0 ; SERVICE_DEMAND_START
        ErrorControl = 1 ; SERVICE_ERROR_NORMAL
        ServiceBinary = %12%\usbuhci.sys
        LoadOrderGroup = Boot Bus Extender

        [ROOTHUB.AddService]
        DisplayName = %ROOTHUB.SvcDesc%
        ServiceType = 1 ; SERVICE_KERNEL_DRIVER
        StartType = 0 ; SERVICE_DEMAND_START
        ErrorControl = 1 ; SERVICE_ERROR_NORMAL
        ServiceBinary = %12%\usbhub.sys
        LoadOrderGroup = Boot Bus Extender

    6-E) usbstor.inf

        Change / Add the bolded lines in the [USBSTOR.AddService] section

        [USBSTOR.AddService]
        DisplayName = %USBSTOR.SvcDesc%
        ServiceType = 1
        StartType = 0
        Tag = 3
        ErrorControl = 1
        ServiceBinary = %12%\USBSTOR.SYS
        LoadOrderGroup = Boot Bus Extender

    6-F) new file: USBBOOT.INF

        Create a new file called USBBOOT.INF in the same directory as your other changed files, and put the following content into it:

        [usbservices]

        HKLM,"SYSTEM\CurrentControlSet\Services\USBSTOR","DisplayName",0x00000000,"USB Mass Storage Driver"
        HKLM,"SYSTEM\CurrentControlSet\Services\USBSTOR","ErrorControl",0x00010001,1
        HKLM,"SYSTEM\CurrentControlSet\Services\USBSTOR","Group",0x00000000,"System Reserved"
        HKLM,"SYSTEM\CurrentControlSet\Services\USBSTOR","ImagePath",0x00020000,"system32\DRIVERS\USBSTOR.SYS"
        HKLM,"SYSTEM\CurrentControlSet\Services\USBSTOR","Start",0x00010001,0
        HKLM,"SYSTEM\CurrentControlSet\Services\USBSTOR","Type",0x00010001,1

        HKLM,"SYSTEM\CurrentControlSet\Services\usbehci","DisplayName",0x00000000,"USB 2.0 Enhanced Host Controller Miniport Driver"
        HKLM,"SYSTEM\CurrentControlSet\Services\usbehci","ErrorControl",0x00010001,1
        HKLM,"SYSTEM\CurrentControlSet\Services\usbehci","Group",0x00000000,"System Reserved"
        HKLM,"SYSTEM\CurrentControlSet\Services\usbehci","ImagePath",0x00020000,"system32\DRIVERS\usbehci.sys"
        HKLM,"SYSTEM\CurrentControlSet\Services\usbehci","Start",0x00010001,0
        HKLM,"SYSTEM\CurrentControlSet\Services\usbehci","Type",0x00010001,1

        HKLM,"SYSTEM\CurrentControlSet\Services\usbhub","DisplayName",0x00000000,"USB2 Enabled Hub"
        HKLM,"SYSTEM\CurrentControlSet\Services\usbhub","ErrorControl",0x00010001,1
        HKLM,"SYSTEM\CurrentControlSet\Services\usbhub","Group",0x00000000,"System Reserved"
        HKLM,"SYSTEM\CurrentControlSet\Services\usbhub","ImagePath",0x00020000,"system32\DRIVERS\usbhub.sys"
        HKLM,"SYSTEM\CurrentControlSet\Services\usbhub","Start",0x00010001,0
        HKLM,"SYSTEM\CurrentControlSet\Services\usbhub","Type",0x00010001,1

        HKLM,"SYSTEM\CurrentControlSet\Services\usbuhci","DisplayName",0x00000000,"Microsoft USB Universal Host Controller Miniport Driver"
        HKLM,"SYSTEM\CurrentControlSet\Services\usbuhci","ErrorControl",0x00010001,1
        HKLM,"SYSTEM\CurrentControlSet\Services\usbuhci","Group",0x00000000,"System Reserved"
        HKLM,"SYSTEM\CurrentControlSet\Services\usbuhci","ImagePath",0x00020000,"system32\DRIVERS\usbuhci.sys"
        HKLM,"SYSTEM\CurrentControlSet\Services\usbuhci","Start",0x00010001,0
        HKLM,"SYSTEM\CurrentControlSet\Services\usbuhci","Type",0x00010001,1

        HKLM,"SYSTEM\CurrentControlSet\Services\usbohci","DisplayName",0x00000000,"Microsoft USB Open Host Controller Miniport Driver"
        HKLM,"SYSTEM\CurrentControlSet\Services\usbohci","ErrorControl",0x00010001,1
        HKLM,"SYSTEM\CurrentControlSet\Services\usbohci","Group",0x00000000,"System Reserved"
        HKLM,"SYSTEM\CurrentControlSet\Services\usbohci","ImagePath",0x00020000,"system32\DRIVERS\usbohci.sys"
        HKLM,"SYSTEM\CurrentControlSet\Services\usbohci","Start",0x00010001,0
        HKLM,"SYSTEM\CurrentControlSet\Services\usbohci","Type",0x00010001,1

         

7) Repack the inf files into their original IN_ format

    If you have not already deleted your extracted .IN_ files, do so now. They need to be replaced. Open a DOS shell again, and navigate to the folder with your changed files. Then exceute the following commands:

    cabarc n USB.IN_ usb.inf
    cabarc n USBPORT.IN_ usbport.inf
    cabarc n USBSTOR.IN_ usbstor.inf

    The three IN_ files should now exist again.

    Congratulations. All out modifications are done.

8) Inject the changed files into the ISO

    Open your Windows CD image again with WinISO. Navigate to the I386 folder, and delete the following files from the ISO, saving the changes to the ISO afterwards:

        * DOSNET.INF
        * TXTSETUP.SIF
        * USB.IN_
        * USBPORT.IN_
        * USBSTOR.IN_

    Just to be sure all is updated in the ISO, cloase and repoen the ISO in WinISO. Now, again go to the I386 folder and select "Add Files". Now add your changed files, in detail:

        * USBBOOT.INF
        * DOSNET.INF
        * TXTSETUP.SIF
        * USB.IN_
        * USBPORT.IN_
        * USBSTOR.IN_

    Save the ISO. You are done.

9) Burn the ISO back to CD

    Feel free to use any burning package you want. I used the free and simple Burnatonce

10) Install Windows XP from the CD

 

    Shut down your computer. Disconnect ANY internal and external hard drives (so Windows cannot find them during installation and mess up their Master Boot Records hehe). Some computers will have trouble to boot without an internal HDD attached, check in your BIOS and, if possible, remove the HDD from the boot sequence and set the USB Harddisk as the first boot device, and the CDROM as second.

    Also, now connect your USB Harddrive directly to the computer, without any Hubs in between.

             

                 

    Windows should install just fine, with the exceptions noted below.

    Issues you will encounter during installation:

        * During driver installation, the USB drivers will prompt you, as they are "not certified" - This is normal. Our changes invalidated the checksum, and therefore the driver is no longer signed. Just press "yes" a couple of times.
        * Upon completion of the install, the system will complain once on the first bootup that the pagefile does not exist. You can ignore this for now, as Windows will work fine without it. People are looking at fixing this issue, but its not critical for now.

 

    Once everything is up and running , shut down and reconnect all your drives.

     

This version of the guide has been tested successfully on the follwoing hardware configurations - please email me your infos if you have successfully completed the guide, so I can add your configuration as well:

 

If you have troubles, please visit the forum dedicated to this tutorial.

have a lot of fun!

Emanuel Schleussinger
[http://www.ngine.de](http://www.ngine.de)
(Tags: windows ) 	
	
		
		
	
User Comments on this article
HUm
by Joe on 30 Apr 2008

      &amp;t=1243 You say: ************************ doh by emanuel on Thu Mar 02, 2006 8:37 am indeed - theres a step missing in my tutorial. There are a few driver INF files in the system that are populated during install from I386/USB*.IN_ (which are simply CAB files containing the usb*.inf driver config). Can you try to boot into BartPE and navigate to your (broken, USB installed) Windows/inf folder (make sure hidden files are shown), and then edit the following files with Notepad so the shown sections look like this: usb.inf: [StandardHub.AddService] DisplayName = %StandardHub.SvcDesc% ServiceType = 1 

Sorry
by Joe on 30 Apr 2008

      Hey sorry I forget the more important thing! I forget to say THANKS ! It's not cause it's not work for me that I don't appreciate your site ! :) 

Great Article
by Jason on 30 Apr 2008

      Worked on the following: Dimmension 3100 Inspiron 9300 Needed to get XP driversfound on the DELL forums for the following: Inspiron 1721 Inspiron 1521 Used Sandisk Micro4GB Cruzer 

Don't work using Win XP Pro SP2
by Joe on 30 Apr 2008

      Hi, First my computer can boot from USB. I try with DOS and all work good. Now I try all what you say and it's work until the computer restart. Then my system Boot again from CD (and so want install Windows again). And I select in my BIOS in Boot sequence: 1- USB (Kingston DataTraveler 4GB) 2- CDROM I don't understand why my system don't boot from USB after that. 

thanks
by zaga on 30 Apr 2008

      It works with xp home sp2 and sp3 on ASUS EeePC, USB hard disk.

---

