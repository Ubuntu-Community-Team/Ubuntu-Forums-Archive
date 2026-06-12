---
title: "How do I get Virt. Win. 7 to use my disk drive, and USB ports"
date: 2011-01-08
forum: General Help
---

### Post by Dangerzone812 on 2011-01-08
Hey all, I'm running Windows 7 through Virtual Box on Ubuntu, and I was wondering how can I have Virtual Windows use my CD drive, so when I pop in a movie, or a CD WMP will read it or something of the sort. Another thing is, how do i get Virtual Windows to read USB drives that I plug in with files I wish to put on it?

Thanks in advance. 

Danger.

---

### Post by Dangerzone812 on 2011-01-08
Hello? :(

---

### Post by howefield on 2011-01-08
For the CD question, try enabling the Passthrough option in your Virtual Machine settings.

For the USB question, which version of VirtualBox are you using ?

---

### Post by Dangerzone812 on 2011-01-09
[IMG]http://img827.imageshack.us/i/screenshotxr.png/[/IMG]

In case the image doesn't show:
[http://img827.imageshack.us/i/screenshotxr.png/](http://img827.imageshack.us/i/screenshotxr.png/)

That obviously doesn't look like what you have. :\

Also I'm using version 3.2.12 r68302

Thanks in advance!

---

### Post by howefield on 2011-01-09
Try highlighting the line where it says VBoxGuestAdditions_3.2.iso and change it to your actual host CD/DVD writer. That should make the "Passthrough" option appear.

Is that version 3.2.12 r68302 OSE edition or PUEL ? If OSE it doesn't have USB support. 

You'd need the PUEL version from the virtualbox website or download version 4 and the extension pack, (as well as guest additions)

---

### Post by Dangerzone812 on 2011-01-10
> **howefield said:**
> Try highlighting the line where it says VBoxGuestAdditions_3.2.iso and change it to your actual host CD/DVD writer. That should make the "Passthrough" option appear.

Is that version 3.2.12 r68302 OSE edition or PUEL ? If OSE it doesn't have USB support. 

You'd need the PUEL version from the virtualbox website or download version 4 and the extension pack, (as well as guest additions)

How do I know if it's PUEL or OSE?

I got it from the actual website if that helps...not from the software center.

Sorry. Total newb :(

---

### Post by LetsMugSanta on 2011-01-10
If it is from the website then it is most likely the puel edition. On the settings of the virutal machine you have to enable usb support and the echi controller. Also go to users and groups in system>administration and select your username and go to advanced settings>user priveleges and enable anything virtualbox or usb support.

When starting the machine also go to devices at the top and install the guest additions.

For future reference the 4.0 version of vbox uses extension packs to enable usb that are available from their website, but you shouldn't need them.

---

