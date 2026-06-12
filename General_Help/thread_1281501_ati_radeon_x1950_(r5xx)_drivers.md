---
title: "ati radeon x1950 (r5xx) drivers"
date: 2009-10-03
forum: General Help
---

### Post by jochem on 2009-10-03
Hello,

I've got an ati radeon x1950 xt, but if I use the "lspci" command in the terminal, it says I'm using a x1900:
07:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900]

I was playing the game "Diablo II" through wine, it works nicely, but only in 2D mode, I can't choose 3D mode.

Which drivers should I use? I'm currently running ubuntu 9.10 beta.
I've read something about ati kernel mode settings, it should support my r5xx card. Is this enabled in ubuntu 9.10? Should I use other drivers?

Thanks in advance

---

### Post by jochem on 2009-10-03
Not resolved yet.

---

### Post by jochem on 2009-10-03
What's the best driver for my card? :(

---

### Post by jochem on 2009-10-03
halp

---

### Post by jochem on 2009-10-04
Bump

---

### Post by oesgur on 2009-10-10
> **jochem said:**
> Bump



bump again. i have the same problem. is there any x1950 drivers for ubuntu

---

### Post by Zoot7 on 2009-10-10
I got this of searching AMD's website:
**[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English")**

Also some of the older ATi cards aren't compatible with the new version of X that's in Jaunty and above. For that you're going to have to downgrade X.
See here:
**[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue]("http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue")**

---

### Post by jochem on 2009-10-11
> **Zoot7 said:**
> I got this of searching AMD's website:
**[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English")**

Also some of the older ATi cards aren't compatible with the new version of X that's in Jaunty and above. For that you're going to have to downgrade X.
See here:
**[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue]("http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue")**

I know, but what are the best open source drivers? And what about Kernel Mode Settings (KMS)? Ubuntu is currently detecting my card as a x1900, but it's a x1950 xt

---

### Post by jochem on 2009-10-11
halp

---

### Post by Zoot7 on 2009-10-12
> **jochem said:**
> I know, but what are the best open source drivers? And what about Kernel Mode Settings (KMS)? Ubuntu is currently detecting my card as a x1900, but it's a x1950 xt
Have a look here for a guide on how to install the open source drivers:
**[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")**

How good/bad they are I have no idea, I've never used them.

---

