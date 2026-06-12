---
title: "Google Earth"
date: 2010-04-11
forum: General Help
---

### Post by Malacath on 2010-04-11
Can anyone please tell me how to install programs?

I'm a total beginner with linux and have just downloaded google earth.
The file that was downloaded has the filename GoogleEarthLinux.bin.
Problem is I don't know what to do with the file.

Clicking it just tell me to choose an application.

I'm using the 64bit version of ubuntu

Thanks in advance.

---

### Post by stilling on 2010-04-11
try this in your terminal window
> sudo apt-get update
sudo apt-get install googleearth

hope this helps

---

### Post by WinterRain on 2010-04-11
Go to system>administration>software sources and open the "other software" tab. Check off "partner" repo, (you don't need to check off the source code option) then it will ask you to reload. Google earth should then show up in the software center. No need for the file you downloaded.

You may also want to add the medibuntu repos also which will give you access to some other stuff. Open a terminal, (applications>accessories>terminal) and copy and paste the following into the terminal, then hit enter and input your password then hit enter again.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by Pablo Pablovski on 2010-04-11
The bin file is the installer, but it needs to be run from a terminal prompt. 

At the folder where your .bin file downloaded to (if in "Downloads", enter cd ~/Downloads then enter:

```
sh GoogleEarthLinix.bin
```

and follow the on-screen destructions.

---

### Post by Malacath on 2010-04-11
> **WinterRain said:**
> Go to system>administration>software sources and open the "other software" tab. Check off "partner" repo, (you don't need to check off the source code option) then it will ask you to reload. Google earth should then show up in the software center. No need for the file you downloaded.

You may also want to add the medibuntu repos also which will give you access to some other stuff. Open a terminal, (applications>accessories>terminal) and copy and paste the following into the terminal, then hit enter and input your password then hit enter again.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Thanks.

I checked off the partner repo but google earth still isn't showing in the software centre.

Am I supposed to do something else to get it to show?

---

### Post by pcdave98 on 2010-04-11
This worked for me:

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

<edit>

It links to this:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

That'll put Google Earth in Software Centre.

---

### Post by stilling on 2010-04-11
try this 

maybe this will help you more 

[http://ubuntuforums.org/showthread.php?t=544064](http://ubuntuforums.org/showthread.php?t=544064)


hope that help you

---

### Post by Malacath on 2010-04-11
Thanks everyone.

I followed the suggestion in one of the links about installing 32bit libraries and then entered the command that was in the first reply and now it's installed and working.

---

### Post by revelationman on 2010-04-13
No matter how many times I tried installing Google Earth I continue to receive this error

Google Earth could not write to the current cache or My Places file location. The values will be set as follows

I have never had this problem before installing google earth just this time 
it is driving me nuts


If anyone has a solution please  post I am pulling out my hair over this 

lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
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
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by Chiapo on 2010-04-13
I just successfully installed Google Earth using the above mentioned method, Software Sources > Other > checked the "Partner" option, then installed the media buntu stuff
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

```
Then clicked "refresh"
Then in terminal
```
sudo apt-get update
```
Then
```
sudo apt-get install googleearth
```

And VIOLA! Google Earth shows up in my Network menu (xubuntu)

---

### Post by mick222 on 2010-04-13
> **Malacath said:**
> Thanks.

I checked off the partner repo but google earth still isn't showing in the software centre.

Am I supposed to do something else to get it to show?
 
 You need to reload the repositories either in synaptic click reload or ```
sudo apt-get update
sudo apt-get install googleearth 
```
in terminal it is better to install via software centre or synaptic as you can uninstall easily and dependences will always be downloaded.

---

### Post by revelationman on 2010-04-13
> **mick222 said:**
> You need to reload the repositories either in synaptic click reload or ```
sudo apt-get update
sudo apt-get install googleearth 
```
in terminal it is better to install via software centre or synaptic as you can uninstall easily and dependences will always be downloaded.

I have done all that but still receive the error I mention so I am wondering if it is hardware issue

Again any advise would be great

---

### Post by revelationman on 2010-04-13
Hello again sorry to post again but I have installed it yet again still having the same error, I have installed Google Earth on another machine and no issue just this one

here is the directory 
google-earth$ dir
drivers.ini		    libflightsim.so	   libmath.so
googleearth		    libfusioncommon.so	   libmeasure.so
googleearth-bin		    libgdal.so.1	   libminizip.so
googleearth-icon.png	    libge_net.so	   libmoduleframework.so
googleearth-mimetypes.xml   libgeobase.so	   libnavigate.so
googleearth.xpm		    libgeobaseutils.so	   libnss_mdns4_minimal.so.2
Google-googleearth.desktop  libGLU.so.1		   libport.so
gpl.txt			    libgoogleearth_lib.so  libproj.so.0
gpsbabel		    libgooglesearch.so	   libQtCore.so.4
ImporterGlobalSettings.ini  libgps.so		   libQtGui.so.4
ImporterUISettings.ini	    libicudata.so.38	   libQtNetwork.so.4
kh20			    libicuuc.so.38	   libQtWebKit.so.4
lang			    libIGAttrs.so	   librender.so
libalchemyext.so	    libIGCore.so	   libreporting.so
libapiloader.so		    libIGExportCommon.so   libwmsbase.so
libauth.so		    libIGGfx.so		   linux
libbase.so		    libIGMath.so	   PCOptimizations.ini
libbasicingest.so	    libIGOpt.so		   plugins
libcollada.so		    libIGSg.so		   qt.conf
libcommon.so		    libIGUtils.so	   resources
libcomponentframework.so    libinput_plugin.so	   shaders
libcurl.so.4		    liblayer.so		   uninstall
libevll.so		    liblayout.so


Is there anything there that looks strange  and why it is giving me this error. 

I have tried to unistall but still there I would love to fix this problem

---

