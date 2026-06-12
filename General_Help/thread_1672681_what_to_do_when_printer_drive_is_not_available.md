---
title: "what to do when printer drive is not available"
date: 2011-01-21
forum: General Help
---

### Post by warakawa on 2011-01-21
I have a fuji xerox docuprint 203A, the printer is not in the database and search does not bring up anything. 

How can I install my printer?

---

### Post by 3Miro on 2011-01-21
Try the manufacturer's web-page and see on Google if anyone has had luck getting this printer to work with a generic driver.

Other than that, you can try Virtual Box. If you print only once in a while, you can install the printer under Virtual Box and use that.

Of course, you can always get a compatible printer, although that costs money, so I guess it should be the last resort.

---

### Post by nomko on 2011-01-21
Try this site:
[http://www.openprinting.org/](http://www.openprinting.org/)
 
and this site:
[http://www.cups.org](http://www.cups.org)
 
And this site:
[http://cups.sourceforge.net/xpp/](http://cups.sourceforge.net/xpp/)

---

### Post by warakawa on 2011-01-21
I am assuming virtual box is run under Windows 7, I am not running dual boot.

---

### Post by anglican on 2011-01-21
> **warakawa said:**
> I have a fuji xerox docuprint 203A, the printer is not in the database and search does not bring up anything. 

How can I install my printer?
I think that is just a PCL5e printer so just choose the generic PCL5e printer driver and it should work.

H

---

### Post by bowens44 on 2011-01-21
> **warakawa said:**
> I am assuming virtual box is run under Windows 7, I am not running dual boot.

No. Virtual box is available in the repositories. No need for dual booting but you do need a valid copy of windows to run in the VM.

---

### Post by warakawa on 2011-01-21
> **anglican said:**
> I think that is just a PCL5e printer so just choose the generic PCL5e printer driver and it should work.

H

nope, when I print the light just blinks and nothing comes out.

---

### Post by warakawa on 2011-01-21
> **bowens44 said:**
> No. Virtual box is available in the repositories. No need for dual booting but you do need a valid copy of windows to run in the VM.

The reason why I use ubuntu is because I can't afford windows 7 and don't want to use it.

---

### Post by nomko on 2011-01-21
> **bowens44 said:**
> No. Virtual box is available in the repositories. No need for dual booting but you do need a valid copy of windows to run in the VM.
 
That version of VirtualBox is the OSE version. You need the non-OSE version which can be downloaded from: [www.virtualbox.org]("http://www.virtualbox.org").
The OSE version has some limitations which the non-OSE version doesn't have.
 
**@waraka:**
Did you looked at the sites i gave you?

---

### Post by anglican on 2011-01-21
> **warakawa said:**
> nope, when I print the light just blinks and nothing comes out.
Which of the 6 options did you try? A bit of googling seems to show that the 203A definitely is a PCL5e printer. Maybe you just have some property for the driver set wrong.

H

---

### Post by reobedr on 2011-01-21
On the fuji xerox website you can find drivers for this printer 
[http://tinyurl.com/6hohat9](http://tinyurl.com/6hohat9)

---

### Post by 3Miro on 2011-01-21
Virtual Box lets you run a copy of Windows under Ubuntu. To get a printer working,  you have to go to the Virtual Box web-page and download their .deb file for Ubuntu 10.10 (or whatever Ubuntu you are using). Under Virtual Box, you don't have to use Windows 7, you can use XP or Vista (assuming you have those).

Other than that, check for a generic driver that can work (see previous posts).

---

### Post by warakawa on 2011-01-21
is there no better way? I don't not wish to run windows at all.

---

