---
title: "Virtualbox WinXP guest can't &quot;see&quot; USB drives"
date: 2010-06-29
forum: General Help
---

### Post by Evanescence on 2010-06-29
I have been using Virtualbox for awhile now and I really like it on Ubuntu. I have Windows XP guest on Ubuntu and I can share files between the two via a shared folder fine. BUT, I have never been able to get the USB drives mounted on Ubuntu to be recognized by the Windows XP :( 
Would anyone please help me to solve this issue.

---

### Post by 3Miro on 2010-06-29
Which version of Virtual Box are you using? The one from the repositories (i.e. Ubuntu Software Center) doesn't have USB support. You need to get the Virtual Box version from the Virtual Box web-page.

If you have already done that, make sure that you are member of the Virtual Box user group. Go to System -> Admin -> Users and Groups, unlock it and make yourself a member of virtual box user group.

---

### Post by Evanescence on 2010-06-29
> **3Miro said:**
> Which version of Virtual Box are you using? The one from the repositories (i.e. Ubuntu Software Center) doesn't have USB support. You need to get the Virtual Box version from the Virtual Box web-page.

If you have already done that, make sure that you are member of the Virtual Box user group. Go to System -> Admin -> Users and Groups, unlock it and make yourself a member of virtual box user group.
Am using version 3.1.8 and I got it from the website, not Ubuntu Software Center. How do I make sure am a member of the virtualbox user group? because when I go to System>Admin>Users and Groups, it's just my account present.

---

### Post by 3Miro on 2010-06-29
> **Evanescence said:**
> Am using version 3.1.8 and I got it from the website, not Ubuntu Software Center. How do I make sure am a member of the virtualbox user group? because when I go to System>Admin>Users and Groups, it's just my account present.

You have to hit Manage Groups button, then find the virtual box users group (it will be vboxusers or something like that), select that and hit Preferences. It will ask for password and then it will allow you to edit the users that are members of that group.

---

### Post by Evanescence on 2010-06-30
> **3Miro said:**
> You have to hit Manage Groups button, then find the virtual box users group (it will be vboxusers or something like that), select that and hit Preferences. It will ask for password and then it will allow you to edit the users that are members of that group.
Hey, thanks! it works fine now and it has been bugging me for quite some time. I appreciate it :)

---

### Post by mirchichamu on 2010-06-30
> **3Miro said:**
> You have to hit Manage Groups button, then find the virtual box users group (it will be vboxusers or something like that), select that and hit Preferences. It will ask for password and then it will allow you to edit the users that are members of that group.

Hi,
I am having the same problem. I made my self as member of the groups but still usb not working. In the lower bar in vmbox the usb icon indicates no usb device attached BUT interestingly in the upper bar in vmbox in devices all my usb devices are present but grayed out. I don't know where is the problem? I need help please.

---

### Post by jimmers on 2010-06-30
MIRCHICHAMU,
Try clicking on the greyed out USB in the top box

---

### Post by mirchichamu on 2010-06-30
> **jimmers said:**
> MIRCHICHAMU,
Try clicking on the greyed out USB in the top box

Thanks jimmers for reply.
Greyed out USB are not responding at all..no surprise.

After restart my other usb are working except my windows mobile for which I installed virtual windows..very sad indeed. Interestingly my HTC device was detected grayed out BUT after installing windows mobile center, that has also disappeared.

---

### Post by livingreality on 2010-12-26
I have similar problem as mirchichamu
I find all my USB-devices on both the "upper menu" and "lower usb icon" in VB, but all greyed out and not working

Using VB 4.0 with guest additions, made active filters for the USB devices i want to use + am part of the vboxusers group.

Help anyone? :)

---

### Post by wilee-nilee on 2010-12-26
> **livingreality said:**
> I have similar problem as mirchichamu
I find all my USB-devices on both the "upper menu" and "lower usb icon" in VB, but all greyed out and not working

Using VB 4.0 with guest additions, made active filters for the USB devices i want to use + am part of the vboxusers group.

Help anyone? :)

Start your own thread in the virtualization part of the forum if you want the best chance of help, also list the USB devices.
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

