---
title: "How to install broadcom b43 driver for bcm4315 card"
date: 2011-08-21
forum: General Help
---

### Post by muhammed irshad on 2011-08-21
Hi,

   I need to install b43 driver for my bcm4315 wifi card. I herd that bcm4315 need a firmware called 
firmware-b43legacy-installer is needed to do this.So how can i install the driver...
Please give step by step procedure...I have installed it once and when i am trying to 
activate it using ubuntu drivers and install it shows error 

system error:archives failed().......Please do help me...Now its not working dont
know why..

---

### Post by gandaran on 2011-08-21
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
connect using wired internet then install from synaptic package manager

---

### Post by muhammed irshad on 2011-08-21
I did everything in the forum...I have found mine is broadcom BCM4312 with pc id 4315 which require 

 **firmware-b43-lpphy-installer**  and i installed it...But even though the b43 driver is not working..Is there any problem with my  **firmware-b43-lpphy-installer** if then how can i solve it...the thing is i could'nt get any error messages while installing...Please help....

---

### Post by dino99 on 2011-08-21
maybe look at it:

[https://help.ubuntu.com/community/WifiDocs/Driver/b43](https://help.ubuntu.com/community/WifiDocs/Driver/b43)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by gandaran on 2011-08-21
> **muhammed irshad said:**
> I did everything in the forum...I have found mine is broadcom BCM4312 with pc id 4315 which require 

 **firmware-b43-lpphy-installer**  and i installed it...But even though the b43 driver is not working..Is there any problem with my  **firmware-b43-lpphy-installer** if then how can i solve it...the thing is i could'nt get any error messages while installing...Please help....
did you remove the previous installed driver and also installed  bcmwl-kernel-source package?

---

