---
title: "Virtualbox USB problem"
date: 2009-07-10
forum: General Help
---

### Post by note32 on 2009-07-10
Hey Guys

        so i installed virtualbox today with WinXP and i can't figure out how to enable USB?](*,)

---

### Post by Ra-Hoor-Khuit on 2009-07-10
What version of Virtual Box did you install?  If you got it from the Ubuntu Repository (via Add/Remove or Synaptic for instance) the version you have does not support USB at all.  You need to have the PUEL licensed version you get from the VB website.  Or is that the version you have?

Here's the tutorial I use when I setting up a new VM.  [http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)  

Don't use the download link in the tut, though, get your copy of VB from here instead (get the PUEL version, NOT the OSE version):

 [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by note32 on 2009-07-10
i have VB3 installed and i i downloaded the i386 from the website for ubuntu 9.04

---

### Post by note32 on 2009-07-10
oh and also when i type this in sudo gedit /etc/init.d/mountdevsubfs.sh i got i into it and i can find this



                         
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

---

### Post by note32 on 2009-07-10
and in /etc/apt/sources.list: i added deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free

---

### Post by PureLoneWolf on 2009-07-10
If you are definitely using the PUEL version - You need to make sure that your user is in the vboxusers group.  After that, logout and back in and USB shouldn't be greyed out anymore.

---

### Post by note32 on 2009-07-10
ok so how do i get to vboxusers group?

---

### Post by note32 on 2009-07-10
i got it to work guys thanks a bunch for all your help):P

---

