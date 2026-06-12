---
title: "How to use Dialup USB modem with Ubuntu 10.10?"
date: 2010-11-20
forum: General Help
---

### Post by DaveReed on 2010-11-20
I have Ubuntu 10.10 booting from a USB stick, and have a U.S. Robotics 56k USB modem that I have not yet been able to use.    

It is at /dev/ttyACM0    

ScanModem found ID 0baf:0303 U.S. Robotics.    

I created a sym link: sudo ln -s /dev/ttyACM0 /dev/modem    

But when I run  
sudo pon  
I get this: 
 /usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'    

Do I also need wvdial and/or GnomePPP, neither of which seem to be present?  (If so, how can I download them via a Windows PC that does already have internet access?)    

Thanks,  
Dave

---

