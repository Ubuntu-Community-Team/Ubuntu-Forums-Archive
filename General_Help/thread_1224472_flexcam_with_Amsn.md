---
title: "flexcam with Amsn"
date: 2009-07-27
forum: General Help
---

### Post by sympaval on 2009-07-27
Hi all,

I've a problem that I don't understand with my webcam.

In fact I've an usb webcam on which it's writed "Speed", I plug it on my pc.
 To test if the webcam can be installed, I typed the command "gstreamer-properties" and get a picture of me displayed in the webcam.

-Linux distribution: ubuntu 8.10
-Kernel version: 2.6.27-14-generic
-the result of command "lsusb":
 Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 002: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam  100    
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

-the result of comand "/sbin/lsmod | grep -i usb:
  usb_storage            83136  0
  libusual               29844  1 usb_storage
  usbcore      149488  7 gspca_spca561, gspca_main,usb_storage, 
   libusual,ohci_hcd,ehci_hcd          
  scsi_mod      155212  5  usb_storage,sr_mod,sd_mod,sg,libata

I didn't see any information about my webcam in the documentation list in ubuntu, and got to google to look for information about Sunplus.
I found a post speaking about "04fc:0561 Sunplus Technology Co., Ltd Flexcam 100" but when I got the download site, all the instructions there were for quickam, qc-usb.

I was confused and decided to try installation with easywebcam2, which detected automatically my webcam "flexcam 100", installed it, and the tests I made were once again positive, I even took a picture of mine.

Then when I tried to use my webcam with amsn, everything come difficult, I can't send the webcam, but I can perfectly receive one from other. When I send the correspondant receive well the invitation, but when He try to connect, it cuts and I receive the message "Impossible d'afficher l'image de la webcam Vérifier qu'elle est bien branchée et installée.Your webcam use a combination of palette/resolution that this extension does not support yet"

I tape "lsmod | grep spca " in the prompt and get this:
gspca_spca561          19328  0
gspca_main             29312  1 gspca_spca561
videodev               41344  1 gspca_main
usbcore               149488  5 gspca_spca561,gspca_main,ohci_hcd,ehci_hcd

I try to follow the instructions given in the documentation to install gspca-spca5xx, I got until the installation of gspca-source package,the build-essential of my kernel version were already installed for the use of easywebcam2.

So at next step of the installation, when I type "sudo m-a a-i gspca", I receive on the configuration screen a "module-assistant, mode interactif" error saying that the gspca-source package construction failed, and at this point I can't continue. I try even in superuser profile, but get the same result.

The "sudo modprobe" command gives nothing, none of gspca and spca module is installed; just the gspca-source package.

I try to test the webcam with vlc streaming, the webcam characteristics are detected, but I when try the stream, the video stoped and noting else happens.

Please I want those who have already got this problem to help me, I think the problem could be with the webcam resolution, but I would like you as usual, to help me go through my problem with these information I gave to you, and help me solving it.

Thanks a lot for all

Eugene.

---

