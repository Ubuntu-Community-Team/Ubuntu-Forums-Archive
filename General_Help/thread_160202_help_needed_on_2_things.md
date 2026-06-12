---
title: "help needed on 2 things"
date: 2006-04-14
forum: General Help
---

### Post by dj-toonz on 2006-04-14
Hi all , got 2 problems ok here goes

1) i've got a jenoptik JD C610 3-in-1 digital camera , connected to the ubuntu box via usb , it does not auto-mount (what i mean by that is , when i plug it in it should pop up gthumb image viewer right to let me download the images of it) it isnt doing, i've checked to see it the camera thingy (dont know what u call it) is set to auto pop up gthunb on camera insert and that's ticked, when i open gthumb up to do it by hand it come's up with ARGUS DC-1510 camera detecated and then it show's no images found (got the camera full) so it's not decteting the correct model of camera in a sense, is there a plugin for gphoto2 to propelly detect the camera model and let me transfer the images? also how do u get the web-cam & movie features of the camera working in Ubuntu? (i dont want to go back to windoze just to use the camera (after i've spent nearly 2 weeks getting unbuntu working how i like it)

2) when the pc boot's up and goes though all the bootup stuff when it get's to the ntp.unbuntulinux.org part it fails (i'm not on a network & not using a router to directly connect to the net). using the speedtouch 330 adsl modem.  is there a way i can disable that part , as i've got the box auto correcting the time as soon as i've logged into the system, i dont want to keep see'ing failed everytime i boot up the machine 

TIA

---

### Post by krismatth3 on 2006-04-14
For #2, look for the entry corresponding to "ntpdate" in /etc/rc2.d/ . It will be something like "S20ntpdate" (sorry I'm at work right now, no access to my system) and then do:

# rm /etc/rc2.d/ntpdatefilename

FWIW, you'll get much more help if you post a topics with relevant titles - most people won't even look at a topic called "help needed". Maybe "camera automount and ntpdate help needed". :)

---

