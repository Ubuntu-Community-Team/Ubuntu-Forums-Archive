---
title: "usb wont mount or only read privileges"
date: 2010-07-13
forum: General Help
---

### Post by Dn4mycrownj on 2010-07-13
This may be some help for others

I have been having a problem with chasing down a permanent fix for the usb thing. I have tried everything I could find for the last 3 hours.
I've exhausted goggle and my brain.  

I have found out this is only a problem in the last two kernels that were released. 

in 10.04 
what i did was remove usbmount in synaptic package manager.
I found to do this in many places. 
That made it so it did not mount or see the flash drives at all. 

The thing that I have been able to do to make it work every time is have the flash drives that i want to use in at boot up. After I do this they auto mount and you have full privileges over the flash drive.  I have removed and reinserted and it still auto mounts and gives full read and write capabilities. 

I really think this might be a kernel issue and not anything else. The issues comes from usbmount not giving the proper privileges to the user.

I cannot find a fix to make them mount no matter what, with the right privileges. It kinda sucks when a friend wants a couple files from you and you have to do a cold boot to be able to load their flash drive.  

Does anyone have any information on this and if there is a fix in the close future. 

Dn4mycrown

---

