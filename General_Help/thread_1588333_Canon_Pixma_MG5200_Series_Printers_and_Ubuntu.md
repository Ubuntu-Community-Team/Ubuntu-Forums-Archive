---
title: "Canon Pixma MG5200 Series Printers and Ubuntu"
date: 2010-10-04
forum: General Help
---

### Post by hitman_dreams on 2010-10-04
Hi all,

I no longer need help finding a driver for my Canon Pixma MG5220 and just wanted to let people know where to find it in case you come across the same problem. Turns out Canon USA doesn't provide ANY Linux drivers at all. So, your options are to find a driver through TurboPrint etc. I stumbled upon this particular driver here:

[http://support-au.canon.com.au/contents/AU/EN/0100301702.html](http://support-au.canon.com.au/contents/AU/EN/0100301702.html)

Canon's Australia site. I also found it on the Canon Asia site, but it was in an .rpm format. I attempted to use alien to convert it (before I found the .deb at the Australia site) and it didn't work. So, there you have it. There is a driver and it works on Ubuntu 10.04 :guitar:

*Mods, if this needs to move elsewhere please let me know thanks.

---

### Post by Snowfiend on 2010-10-25
Awesome! That worked great, just run the install.sh and it walks you through the setup. I set it up for wireless lan and it's working great!!!
Thanks for posting the link to the drivers!

---

### Post by eaglez69 on 2010-10-30
woo! google finally linked me to this page! It's always a matter of finding the right keywords.. :)

Thanks for the find! Did you ever manage to get the scan function working with sane or something similar?

---

### Post by JLH02 on 2010-11-04
Hitman,  thank you very much for the link.  Install on 10.04 went smooth, I have it set up over a wireless network now.

I also was able to get the scan function working over wireless using drivers from the same site.

ScanGear MP documentation
[http://support-au.canon.com.au/contents/AU/EN/0300410801.html](http://support-au.canon.com.au/contents/AU/EN/0300410801.html)

ScanGear MP software (debian package)
[http://support-au.canon.com.au/contents/AU/EN/0100303002.html](http://support-au.canon.com.au/contents/AU/EN/0100303002.html)

It's not great software, but it works.  You can either launch scangear from within GIMP or at the command line:

```
 joe-laptop ~$scangearmp & 
```It gave me an error message on the first launch, all I had to do was tell it to update the scanners list.

---

### Post by boson007 on 2010-11-07
Just had to replace my PIXMA MP600 printer and bought the PIXMA MG5220. I'm so fortunate to have found this post, because I was just unable to install it properly. THANK YOU GUYS! I'm still experiencing minor issues. I might post some further questions. But for now, any ideas how to have the scan recognized by XSANE? Otherwise, scangearmp is working and provides a temporary solution.

---

### Post by cheri703 on 2010-12-15
I tried to install this driver, using the install.sh, and it keeps erroring out. I searched the error and got this thread: [http://ubuntuforums.org/showthread.php?t=1475336](http://ubuntuforums.org/showthread.php?t=1475336) , but the solutions there didn't help either.

I just bought this printer, feeling confident in the fact that there's a driver for it, and now I can't get it installed. I did just install the 2 .deb files, but I'm hoping there's more functionality available than that. I can't adjust print quality, I can't get about 90% of the settings from it. Perhaps I need to just accept that a linux driver won't have anywhere close to the functionality of a windows driver, but...this is disappointing. :(

Anyone have any errors when installing, and any ideas why I might be? After taking the steps in that other thread, I got "An error occurred. A necessary package could not be found in the proper location."

I am running 10.04, netbook edition, but not running a une session, regular desktop session. 

I have no idea what the issue might be, any help would be greatly appreciated.

---

### Post by LinuxGuy2.5 on 2010-12-19
Thanks... these drivers work great.  The commenter above that stated that some settings aren't available... Most settings are available for the printer within any decent program that you may be printing from.  The only useful thing that I see not working is the ink level indicators - which are on the print itself as well... so no big deal.

The one thing I would like to be working though, that doesn't seem to have a Linux equivalent is the CD printing for this printer.  You can install the CD Label printer via Wine, but it reports no compatible printer available and will not start.

Does anyone know of a CD printing program for Linux that is compatible with this printer?

Thanks to everyone... especially Hitman for finding the drivers!

LinuxGuy

---

### Post by Natume on 2010-12-27
Just wanted to confirm : drivers appear to work perfectly on Maverick Meerkat.  (That said, I haven't tested any advanced features yet.)

Thanks for the heads up!  I just got one of these for my family for Christmas (Windows folks) and was debating getting one for myself if I was able to get it working through my laptop.

---

### Post by benjaminelzerman on 2010-12-27
I downloaded scangearmp-source-1.60-1.tar.gz from the link above.  I found .../scripts/install.sh and ran it, but got "An error occurred. The package management system cannot be identified."  I am running Ubuntu 10.04 64bit.  can anyone help?

Then I downloaded the Debian package of scangearmp and got the same error while trying to run install.sh, so I installed the two .deb packages (for 64bit).  Still nothing.  What am I doing wrong?

---

### Post by dandaman96 on 2010-12-28
Another FYI...  

I'm on Natty - 11.04.  

Both the print driver and the scan tool work great for me.  

Ran both install.sh as root.  Confirmed scan and print works from user accounts.  

Thanks to the original poster for the links.

---

### Post by mabahoangpuetmo on 2011-01-04
> **cheri703 said:**
> I tried to install this driver, using the install.sh, and it keeps erroring out. I searched the error and got this thread: [http://ubuntuforums.org/showthread.php?t=1475336](http://ubuntuforums.org/showthread.php?t=1475336) , but the solutions there didn't help either.


> **benjaminelzerman said:**
> I downloaded scangearmp-source-1.60-1.tar.gz from the link above.  I found .../scripts/install.sh and ran it, but got "An error occurred. The package management system cannot be identified."  I am running Ubuntu 10.04 64bit.  can anyone help?


Hey, i believe i was having the same issues as the two of you.

Using the link cheri703 provided i was able to edit the install.sh file to allow me to install the packages. All i did was comment out the lines of code hinted at from cheri's link:

lines 1256-1269:
```

#if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
	#	printf "$L_INST_COM_01_02"
	#	return $C_ERR_CODE
	#else
	#	if test $c_system_rpm -eq 0; then
	#		C_system="rpm"
	#		C_arch32="i386"
	#		C_arch64="x86_64"
	#	else
			C_system="deb"
			C_arch32="i386"
			C_arch64="amd64"
	#	fi
	#fi

```

line 1550:
```

C_FUNC_show_and_exec "sudo dpkg --force-architecture -iG $c_fpath_pkg_name"

```

and line 1740:
```

C_FUNC_show_and_exec "sudo --force-architecture dpkg -P $1"

```

I apologize in advance if posting a link to a file is against forum rules; This is my first post. Just replace the original install.sh file with this one:
[http://www.megaupload.com/?d=E5NA89AH](http://www.megaupload.com/?d=E5NA89AH)

good luck.

---

### Post by eljopc on 2011-01-04
> **dandaman96 said:**
> Another FYI...  

I'm on Natty - 11.04.  

Both the print driver and the scan tool work great for me.  

Ran both install.sh as root.  Confirmed scan and print works from user accounts.  

Thanks to the original poster for the links.

I installed the scan software in 10.10 with the software center but the xsane scanner software does not find  the wifi scanner? What goes wrong? Do I have to activate it somehow?

---

### Post by convert_mrta on 2011-01-04
> **benjaminelzerman said:**
> I downloaded scangearmp-source-1.60-1.tar.gz from the link above.  I found .../scripts/install.sh and ran it, but got "An error occurred. The package management system cannot be identified."  I am running Ubuntu 10.04 64bit.  can anyone help?

Then I downloaded the Debian package of scangearmp and got the same error while trying to run install.sh, so I installed the two .deb packages (for 64bit).  Still nothing.  What am I doing wrong?
Benjamin,  I experienced the same error.  Have you been able to resolve?   Can anyone help?

greg@greg-laptop:~/Downloads/Cannon MG5225 Driver/cnijfilter-mg5200series-3.40-1-deb$ sudo ./install.sh
==================================================

Canon Inkjet Printer Driver Ver.3.40-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
An error occurred. The package management system cannot be identified.
greg@greg-laptop:~/Downloads/Cannon MG5225 Driver/cnijfilter-mg5200series-3.40-1-deb$

---

### Post by mabahoangpuetmo on 2011-01-05
> **convert_mrta said:**
> Benjamin,  I experienced the same error.  Have you been able to resolve?   Can anyone help?


Try this install.sh file:
[http://www.megaupload.com/?d=E5NA89AH](http://www.megaupload.com/?d=E5NA89AH)

You can read my previous post to see what i changed. I used this to install drivers for my Pixma MG5220 on Ubuntu 9.10

---

### Post by dkh503 on 2011-02-05
Just wanted to thank everyone for contributing to this thread. I was able to get a Canon MG5220 all-in-one installed on Xubuntu (Lucid) on an old Compaq Presario with a 600MHz Celeron. The computer is owned by a gentleman with psychological challenges, and I try to help him keep this old machine running. Unfortunately, he purchased his printer/scanner before having me consult the compatible hardware list, and it looked liked we would not be able to install this printer, until I found this thread. The all-in-one appears to have all of its functionality after following the instructions provided here and in the attached links. Just remember, you never know who you are helping when you contribute.

---

### Post by Remanifest on 2011-02-08
Thanks to all the contributors of this thread... initially I had the problem with the package manager not being recognized, so I commented out the lines as directed, and everything worked as it should.  For the scanner program, I only needed to comment out lines 194-207 of install.sh

When I was done, lines 194-207 of install.sh in the scangearmp folder contained the following lines of code:

```

        #if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
        #       printf "$L_INST_COM_01_02"
        #       return $C_ERR_CODE
        #else
        #       if test $c_system_rpm -eq 0; then
        #               C_system="rpm"
        #               C_arch32="i386"
        #               C_arch64="x86_64"
        #       else
                        C_system="deb"
                        C_arch32="i386"
        #               C_arch64="amd64"
        #       fi
        #fi

```


I also commented out line 678 of the same file, so that it would read as follows:

```

                        #C_FUNC_show_and_exec "sudo dpkg -P $1"

```

Whether you want to comment out that second bit of code or not is up to you... it has to do with uninstall, though.

Again, thanks to everyone else who has made the installation of this printer a breeze... your direction and advice has saved me a lot of hunting around on my own!

---

### Post by gmutlu on 2011-02-24
Those who get "The package management system cannot be identified" error should remove "rpm" package from their ubuntu installation because installation script fails if both "rpm" and "deb" packages are installed on the machine. I think they can install "rpm" if they need it after installation.

---

### Post by rewyllys on 2011-03-03
> **hitman_dreams said:**
> Hi all,

I no longer need help finding a driver for my Canon Pixma MG5220 and just wanted to let people know where to find it in case you come across the same problem. Turns out Canon USA doesn't provide ANY Linux drivers at all. So, your options are to find a driver through TurboPrint etc. I stumbled upon this particular driver here:

[http://support-au.canon.com.au/contents/AU/EN/0100301702.html](http://support-au.canon.com.au/contents/AU/EN/0100301702.html)

Canon's Australia site. . . . So, there you have it. There is a driver and it works on Ubuntu 10.04 :guitar:

. . . .

Many thanks, hitman.  From driver download to successful test print page took me less than 10 minutes.  Hurray once again for the Ubuntu Forums!:popcorn:

---

### Post by PZJM on 2011-03-27
Just picked myself up a Canon Pixma MG5220 because it was on sale at Best Buy for $99.  The drive worked and I'm able to print and scan.  However, the functionality from the LCD screen is a bit off.  I'm trying to use the scan feature from the LCD screen on the printer and I can't seem to get it to work.  I know it's a trivial issue but I'm one of those folks who will not give up.  Has anyone had success using the LCD screen features?  For example, scan to PDF?

Thanks Hitman...

---

### Post by PZJM on 2011-03-27
I have one more question if this thread is still alive.  If I plug my printer into the wireless router (via ethernet cable) technically I should be able to access the printer from my ethernet connected desktop and wireless laptop (both running Ubuntu 10.10 64bit).

Currently, my wireless printer is connected directly to my desktop via usb.  However, I want to make my wireless printer available to all computers in the house.  I'm thinking that connecting my wireless printer to the router will all me to share the printer between computers?  Does this sound correct?  Also, would I need to uninstall the current driver or just run the setup again.

Any help would be greatly appreciated.

---

### Post by JLH02 on 2011-03-28
> **PZJM said:**
> I have one more question if this thread is still alive.  If I plug my printer into the wireless router (via ethernet cable) technically I should be able to access the printer from my ethernet connected desktop and wireless laptop (both running Ubuntu 10.10 64bit).

Currently, my wireless printer is connected directly to my desktop via usb.  However, I want to make my wireless printer available to all computers in the house.  I'm thinking that connecting my wireless printer to the router will all me to share the printer between computers?  Does this sound correct?  Also, would I need to uninstall the current driver or just run the setup again.

Any help would be greatly appreciated.

The MG5200 has built in wireless networking.  You can connect it to your wireless router through the settings in the printer's control panel / LCD screen.  I'm not sure mine even has an ethernet port (it's 3 floors down and I'm too lazy to go look).  

I've never used my MG5200 with any of my computers (Ubuntu 10.10 and Win7) other than over the wireless network.  You may want to assign it a static IP.  I did, not sure if letting it use DHCP could/would cause any issues.

I doubt that you'll need to uninstall the driver.  For Ubuntu, just try System->Administration->Printing.  Click the Add button.  Expand the Network Printer option on the left and wait a few (1-10) seconds.  It should refresh and show the Canon-MG5200-series_xx-xx-xx-xx-xx-xx.  Select that printer, click Forward, it should search for and find the driver.

---

### Post by bcooley on 2011-04-20
Link still works great and thank you for directing to useful download. Set it up on the network directly without using a USB cable to start with. 
THANKS AGAIN

---

### Post by hitman_dreams on 2011-04-30
Holy cow guys! So glad I wasn't the only one having trouble with this. Didn't think it would get this much attention really. I myself haven't run into many issues...but I don't use the scanner, just copy and print. I don't frequent here as much as I do the Android forums on XDA, so sorry if I missed questions. Looks like others took over for me while I wasn't paying attention to this thread. A big thanks to YOU all! Glad to help :D

---

### Post by bpayne71 on 2011-05-19
Thanks to the original poster for putting up the link to this driver.  I was getting very frustrated because I could not get my MG5220 to work; until I found this link.  Ran the install.sh in terminal and it works great now.  Thank you again!!

---

### Post by nwstephens on 2011-10-29
Yes, the MG5200 series IJ Printer Driver Ver. 3.40 for Linux works great. The install.sh ran beautifully. I wish all my printers were this easy.

---

### Post by emeraldgirl08 on 2011-11-03
I've never run an .sh script before!

Is there a kind person who will guide me through this process??? 

I need my MG5220 setup for school. TIA :)

**EDIT:**

Nevermind. I got it working! I had to use search but the answer is here in the forums for beginning ubuntu users. That installs the driver to use the copier and printer. I got my ThinkPad to connect with it wirelessly. I also used the "scangearmp" link to download and install the driver for the scanner. Doesn't work with "simple scan." I have to open terminal and type in the command to get the canon scan "GUI" to appear. Doesn't bother me at all tho :)

Thanks to the people who contributed and found answers on this thread!

---

### Post by mrcpuhead on 2011-11-25
> **JLH02 said:**
> Hitman,  thank you very much for the link.  Install on 10.04 went smooth, I have it set up over a wireless network now.

I also was able to get the scan function working over wireless using drivers from the same site.

ScanGear MP documentation
[http://support-au.canon.com.au/contents/AU/EN/0300410801.html](http://support-au.canon.com.au/contents/AU/EN/0300410801.html)

ScanGear MP software (debian package)
[http://support-au.canon.com.au/contents/AU/EN/0100303002.html](http://support-au.canon.com.au/contents/AU/EN/0100303002.html)

It's not great software, but it works.  You can either launch scangear from within GIMP or at the command line:

```
 joe-laptop ~$scangearmp & 
```It gave me an error message on the first launch, all I had to do was tell it to update the scanners list.

First, many thanks to hitman and others that helped solve the print & scan driver "mystery" for PIXMA devices!  If you're using the GNOME desktop, and want a shortcut for the ScanGear program on the Applications menu, here's a link with instructions:

[http://library.gnome.org/users/user-guide/stable/menu-editor.html.en]("http://library.gnome.org/users/user-guide/stable/menu-editor.html.en")

---

### Post by Aggiepride2003 on 2011-12-31
> **nwstephens said:**
> Yes, the MG5200 series IJ Printer Driver Ver. 3.40 for Linux works great. The install.sh ran beautifully. I wish all my printers were this easy.

**Canon MG 5220 Printer** 			 			 			 		   		 		 		Hi Everyone,  I'm very very new to this.  I have Linux and Ubuntu and I'm trying to  just hook up my Canon Printer to my computer.  I"m getting very  frustrated.  I've seen posts concerning hooking up this printer to a  computer.  However, I'm very confused.  Can anyone help me out, like  step by step sorry.

---

### Post by LordBam! on 2012-01-15
I guess this is a quasi bump. I'm just making any others aware that it works for printing on Ubuntu 11.10 64. Haven't tried scanning yet but will try to get to that at a later date.

---

### Post by LordBam! on 2012-01-15
> **Aggiepride2003 said:**
> **Canon MG 5220 Printer** 			 			 			 		   		 		 		Hi Everyone,  I'm very very new to this.  I have Linux and Ubuntu and I'm trying to  just hook up my Canon Printer to my computer.  I"m getting very  frustrated.  I've seen posts concerning hooking up this printer to a  computer.  However, I'm very confused.  Can anyone help me out, like  step by step sorry.

No prob, this is what worked for me. Download this:

[http://support-au.canon.com.au/conte...100301702.html](http://support-au.canon.com.au/conte...100301702.html)

extract it. Look inside the folder for the file named "install.sh" Double click it and then select run in terminal. Don't be afraid of the GUIless install just read the prompts and respond as fits your situation. Even works for the wireless install.

Good Luck!!

---

### Post by campbuds on 2012-03-08
> **hitman_dreams said:**
> Hi all,

I no longer need help finding a driver for my Canon Pixma MG5220 and just wanted to let people know where to find it in case you come across the same problem. Turns out Canon USA doesn't provide ANY Linux drivers at all. So, your options are to find a driver through TurboPrint etc. I stumbled upon this particular driver here:

[http://support-au.canon.com.au/contents/AU/EN/0100301702.html](http://support-au.canon.com.au/contents/AU/EN/0100301702.html)

Canon's Australia site. I also found it on the Canon Asia site, but it was in an .rpm format. I attempted to use alien to convert it (before I found the .deb at the Australia site) and it didn't work. So, there you have it. There is a driver and it works on Ubuntu 10.04 :guitar:

*Mods, if this needs to move elsewhere please let me know thanks.

Can I just say Thank you!!! I just bought this printer yesterday and wasn't thinking about my Ubuntu laptop. ](*,)

---

### Post by rewyllys on 2012-03-08
Here is another source of instructions for installing the Canon Pixma MG5220 in Linux:

[http://linuxtidbits.wordpress.com/2011/07/14/canon-pixma-mg5220-ubuntu-setup/]("http://linuxtidbits.wordpress.com/2011/07/14/canon-pixma-mg5220-ubuntu-setup/")

Just 10 minutes ago I finished using these instructions, posted by Todd Partridge.  They are simple and straightforward, and they worked beautifully for me in Linux Mint 11.

Thank you, Mr. Partridge!:D

BTW, he found his source for the Linux drivers at the following URL:

[http://software.canon-europe.com/software/0040259.asp]("http://software.canon-europe.com/software/0040259.asp")

---

### Post by Cycledoc on 2012-03-16
The source in Australia worked fine for me--from first post 
[http://support-au.canon.com.au/conte...100301702.html]("http://support-au.canon.com.au/contents/AU/EN/0100301702.html")

I'm using a XPS 15 and 11.10.

Thanks for finding the driver.  Installation a cinch even for an elderly newby with his new computer.

---

### Post by rvaliant on 2012-03-27
Has anyone been able to get b&w working?

---

### Post by Davidchsw on 2012-04-10
I can get the scanner function to work from GIMP. The computer shows the printer, but I am never able to get it to print anything. Funny thing is the computer found my wife's HP printer and it worked over wifi without downloading any drivers. She has not been able to get it to consistently work over wifi in Windows. Thanks for any help.

---

### Post by red436 on 2012-05-24
@benjaminelzerman
"An error occurred. The package management system cannot be identified."
change C_FUNC_get_system() in the install.sh files to 
```
C_FUNC_get_system()
{
    local c_system_rpm=""
    local c_system_deb=""

    C_system="deb"
    C_arch32="i386"
    C_arch64="amd64"
    
    return 0
}
```

---

### Post by Atanas@ on 2012-05-30
Applying the following patch (ids taken from the latest unreleased sane-backends) and rebuilding the libsane package from source seems to make (x)sane recognize and work with my MG5250 scanner.

--- pixma_mp150.c-dist	2011-01-16 02:01:28.000000000 +0100
+++ pixma_mp150.c-new	2012-05-23 10:30:37.000000000 +0200
@@ -162,6 +162,11 @@
 #define MX350_PID 0x1742
 #define MX870_PID 0x1743
 
+/* 2010 new devices (untested) */
+#define MG5100_PID 0x1748
+#define MG5200_PID 0x1749
+#define MG6100_PID 0x174a
+
 /* Generation 4 XML messages that encapsulates the Pixma protocol messages */
 #define XML_START_1   \
 "<?xml version=\"1.0\" encoding=\"utf-8\" ?>\
@@ -1653,5 +1658,10 @@
   /* Generation 4 CCD */
   DEVICE ("Canon MP990 series", "MP990", MP990_PID, 4800, 638, 877, PIXMA_CAP_CCD | PIXMA_CAP_TPU),
 
+  /* Latest devices (2010) Generation 4 CIS/CCD */
+  DEVICE ("Canon PIXMA MG5100", "MG5100", MG5100_PID, 1200, 638, 877, PIXMA_CAP_CIS),
+  DEVICE ("Canon PIXMA MG5200", "MG5200", MG5200_PID, 2400, 638, 877, PIXMA_CAP_CIS),
+  DEVICE ("Canon PIXMA MG6100", "MG6200", MG6100_PID, 2400, 638, 877, PIXMA_CAP_CIS),
+
   END_OF_DEVICE_LIST
 };

Had to add the scanner IP to /etc/sane.d/pixma.conf.

Xsane now works, but I find particularly useful the simple-scan package (which also depends on the sane backend).

I wonder why it takes so long for the sane folks to release an updated version, those are printer models from 2010 after all.

---

### Post by Mud Pie on 2012-06-02
Hello everyone,

While I do not own a Canon MG5200 Series printer, I own a Canon Pixma MP495.  I figured the steps to set it up had to be similar.  I went to the Aussie web site and found the proper Linux drivers for my printer.  I tried the US Canon web site a while back and found no Linux drivers; I wrote my printer off as a "nope".

I downloaded the Aussie drivers, installed, and started printing (using wireless, I might add)  RIGHT away !!

This site is awesome, downright awesome !!

---

### Post by otetiani on 2012-10-15
thanks everyone who posted tips here! 

Had some operability with my MG5220, but now everything works (though selecting the paper tray is not easy).

---

### Post by gtippitt on 2013-01-06
Similarly, I've got a Canon MG3122 printer & scanner ($50 at WalMart) with USB and WiFi.  I had to have a Windoze machine to setup the device on my wireless network , but then UBUNTU found the printer without any problem. I couldn't scan until I found this thread and looked on the Canon Asia site to find the ScanGearMP for the 3100.  The link below has the Deb file to download and install.  It does pretty much what you need from a scan program.  Thanks for pointing us East to find the fixes we needed.

[http://support-sg.canon-asia.com/contents/SG/EN/0100394102.html]("http://support-sg.canon-asia.com/contents/SG/EN/0100394102.html")

---

### Post by AmpersUK on 2013-05-14
Alas, they've done something differently in 13.04 and the driver won't load, either using the PPA or the Software centre. All of a sudden I don't have a printer.

---

### Post by pdc on 2013-05-14
If you delete any existing printers set up ..as they don't seem to work..

from the Canon Asia site

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100301702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100301702.html)

the driver package comes down as [COLOR="#008000"]cnijfilter-mg5200series-3.40-1-deb.tar.gz[/COLOR] .......if you download this and select "SAVE" to your downloads folder

What happens if you paste these commands into a terminal?

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mg5200series-3.40-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mg5200series-3.40-1-deb[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

......that should have you up and running ...........

you can check that it is installed by the command

> [COLOR="#FF0000"]sudo dpkg -l | grep cnijfilter[/COLOR]

---

