---
title: "Setting up FGLRX in 9.04 error?"
date: 2010-01-02
forum: General Help
---

### Post by Pesky_Programmer on 2010-01-02
I used to have Jaunty installed, this was when it was still being updated, and was able to get fglrx to work using this site.

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

To make a long story short I lost my 9.04 install and have recently reinstalled it because I found Karmic to be unstable.

This still works up until the point where I reinstall the xserver. After typing in 
"sudo apt-get install xserver-xorg fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx libdrm2=2.3.1-0build1 gnome-session fast-user-switch-applet=2.24.0-0ubuntu6"

I get this error.

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xorg-driver-fglrx: Depends: lib32gcc1 but it is not going to be installed
                     Depends: libc6-i386 but it is not going to be installed
E: Broken packages


I assume this is because I am trying to get packages from intrepid which is so old now that they are no longer being hosted. If this is the case can I find these files somewhere else? 
Thanks for reading and for any advise you have to offer.

I have already removed the xserver so I would like to resolve this before I have to reboot/shutdown my computer as I will be without a GUI.

EDIT: I think I found a way to reinstall the xserver for jaunty and since it is late where I am will call it a night. Hopefully when I boot back up in the morning I will have a GUI still.

---

