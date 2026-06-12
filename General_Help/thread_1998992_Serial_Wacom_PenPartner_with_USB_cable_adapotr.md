---
title: "Serial Wacom PenPartner with USB cable adapotr"
date: 2012-06-07
forum: General Help
---

### Post by Lester Paul on 2012-06-07
Hi, to all. This is my problem. I have an old Serial Wacom PenPartner (Model CT-0405-R), that I used to use a while ago with another computer running earlier versions of Ubuntu. I have not used it for long time and I decided to connect it to a newer computer running Ubuntu 12.04 which does not have a Serial port. I have connected a Sabrent USB to Serial adapter cable to the tablet to interface with the computer. The cable seems to be recognized under lsubd, and the tablet is powered up. The Tablet itself however is not being detected at all. Can anyone steer me in the right direction with this problem?

---

### Post by Favux on 2012-06-07
Hi Lester Paul,

Welcome to Ubuntu forums!

Support for the Wacom serial graphics tablets was dropped with the switch to xf86-input-wacom for X Server 1.7, i.e. Lucid 10.04.

So we developed work arounds.  [HOW TO Set Up a Wacom Serial Tablet in Ubuntu]("http://ubuntuforums.org/showthread.php?p=10928556#post10928556") will help you set up your PenPartner.  For Precise you use the new wacom_serial.ko serio driver.

I don't recognize the Sabrent USB to Serial adapter cable.  Hopefully that will be fine.

Early on we did have to modify the kernel drivers for a couple of convertors to get them working with the Wacom tablets.  But I think most if not all of the converter drivers have been updated with Precise's 3.2 kernel.  If not there are some posts on the thread that show you how to do it.

---

