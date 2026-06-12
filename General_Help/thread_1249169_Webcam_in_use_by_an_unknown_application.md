---
title: "Webcam in use by an unknown application"
date: 2009-08-25
forum: General Help
---

### Post by Monkey77 on 2009-08-25
I am running ubuntu 9.04 and have had my Logitech Quickcam pro 3000 working just fine until just recently.

The camera light is always on and no software can get access to it.  I use Pidgin, skype, cheese or Camorama.

Within the messages log the driver is loading just fine:
Aug 25 06:32:55 phil-desktop kernel: [   10.228513] pwc: Philips webcam module version 10.0.13 loaded.
Aug 25 06:32:55 phil-desktop kernel: [   10.228516] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
Aug 25 06:32:55 phil-desktop kernel: [   10.228518] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
Aug 25 06:32:55 phil-desktop kernel: [   10.228520] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
Aug 25 06:32:55 phil-desktop kernel: [   10.228539] pwc: Logitech QuickCam Pro 3000 USB webcam detected.
Aug 25 06:32:55 phil-desktop kernel: [   10.253194] pwc: Registered as /dev/video0.
Aug 25 06:32:55 phil-desktop kernel: [   10.257999] usbcore: registered new interface driver Philips webcam

What I would like to know is how to find out who has the /dev/video0 file open?

I have tried shutting down all applications that might be using it.

---

### Post by prshah on 2009-08-25
> **Monkey77 said:**
> 
What I would like to know is how to find out who has the /dev/video0 file open?

You can check which application has the file (devices are files too) "/dev/video0" open with the command ```
lsof | grep video0
``` Add "sudo" in front if you dont get any output.

Note: lsof will take a few seconds (between 15-45), so please be patient.  Your system has _not_ jammed.

Please post back here with output / error if any in case you require further assistance.

---

### Post by Monkey77 on 2009-08-25
Thanks for the quick reply, the output was:

phil@phil-desktop:~$ sudo lsof | grep video0
[sudo] password for phil: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/phil/.gvfs
      Output information may be incomplete.

Which is most odd.  I was expecting something to come out of it.

Not sure where to look next.  If the file is not in use but the light is on that is most strange...

---

### Post by gradinaruvasile on 2009-08-25
Plug it out and back in. And then test with 

gstreamer-properties

in a terminal. Go to video tab, select device pc camera (or whatever u have besides default), press test.

---

### Post by Monkey77 on 2009-08-25
Thank you for the response:

This was the result:

Video for Linux 2 (v4l2): Could not open device "/dev/video0" for reading and writing.

---

### Post by gradinaruvasile on 2009-08-25
Did u unplug it and plugged back in?
What is the device name? PC Camera?

Also, post the output of 

ps ax

in a terminal.

also

ls -al /dev/video0

---

### Post by Monkey77 on 2009-08-26
Most strange, the camera is working perfectly today.  I have not run any updates and only rebooted since I last posted!?!?

I did unplug the camera and wait 10 seconds before plugging it.

The gstreamer-properties reported the device as "Unknown", I tried both default and unknown and got the same error.  However this morning the device is showing up as "Logitech Quickcam Pro 3000".

The device is in the same USB port.  All software that I was running yesterday is running today.  Only difference is that I have no stepped away from the PC yet so that the system has a chance to go into standby...

Many thanks for your assistance, I will have to wait and see if it happens again.

---

