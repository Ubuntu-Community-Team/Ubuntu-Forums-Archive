---
title: "resolution? help a skitty out"
date: 2009-11-11
forum: General Help
---

### Post by Hydrofarmer on 2009-11-11
Very new to ubuntu and I cant figure out how to change the resolution. 

Pics would help

---

### Post by flugo on 2009-11-11
> **Hydrofarmer said:**
> Very new to ubuntu and I cant figure out how to change the resolution. 

Pics would help

Sorry no pics. which distro do you have running, ubuntu? you will need to load the drivers for your video card. in ubuntu on a new install it should pop up and ask you if you want to load new video drivers. look in the upper right of the top panel on your desktop.

---

### Post by Hydrofarmer on 2009-11-11
9.10

---

### Post by Kennycl on 2009-11-11
If you click System..Preferences..Display is the resolution you want in there?

---

### Post by Hydrofarmer on 2009-11-11
I have looked at other threads and have to add the resolution. The resolution I want isn't given as an option. I have to go to the xorg.conf or something. Plus i have the nvidia driver  already

---

### Post by Kennycl on 2009-11-11
I shall have to let someone else help you them I'm afraid, not worked with Nvidia at all!

(And only been on here for a couple of days myself!)

Kenny

---

### Post by Hydrofarmer on 2009-11-11
Ok i know I have to configure something in xorg.conf. dont know what pls help

---

### Post by Hydrofarmer on 2009-11-11
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

How do i fix this ?!?!?

---

### Post by norwoods on 2009-11-11
open a terminal and run the program. the gksu runs the program as root
Applications>>Accessories>>Terminal
type gksu nvidia-xconfig <Enter>
enter your password

reboot

open a terminal
Applications>>Accessories>>Terminal
type gksu nvidia-settings <Enter>
enter your password

this will allow you to change the configuration. be sure to save the configuration if you change it.

---

### Post by Hydrofarmer on 2009-11-11
norwoods i appreciate the help. I downloaded that gnome shell, restarted AND POOF my res was back to normal even higher than i had it B4. As far as what that downloading it did I have know Idea. BUT i would love to know how downloading that shell fixed it?

Can u tell me why the shell fixed the problem?

---

### Post by norwoods on 2009-11-12
i would love to know how downloading that shell fixed it also.

---

### Post by Giblet5 on 2009-11-12
> **norwoods said:**
> i would love to know how downloading that shell fixed it also.

I'm pretty sure that it was all of the other things done, but not mentioned, that fixed the problem. :)

---

