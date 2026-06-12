---
title: "can't install with my nvidia card"
date: 2005-02-09
forum: General Help
---

### Post by thelastone on 2005-02-09
I have an nvidia agp card (riva tnt2) And an ecs kt-600a motherboard. Everytime I try to install or run the live cd, I get to the point of the x server starting up and the computer freezes.  on the live cd I pushed control, alt and f2. It says it is using the vanta [nv6] driver for the video card. What can I do to use my nvidia card?

I have an old s3 cirrus logic pci card and I am using that. I tried downloading the nvidia driver and installing it and doing the "sudo dpkg-reconfigure xserver-xfree86" command to reconfigure the x settings. I also changed the /etc/modules and added the word nvidia. And I also added Load "nvidia" to the /etc/x11/xf86config-4 and deleted the Load "Glcore". When I rebooted It crashed at loading x and gives the error (EE) No devices detected.  So much for doing it the round about way. 
Is there any way to just have my nvidia card work? Any help would be great.
Thanks
Chad

---

