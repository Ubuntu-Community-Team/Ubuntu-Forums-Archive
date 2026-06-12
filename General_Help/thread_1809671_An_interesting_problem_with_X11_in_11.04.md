---
title: "An interesting problem with X11 in 11.04"
date: 2011-07-21
forum: General Help
---

### Post by dagamant on 2011-07-21
X11 does not start when ubuntu 11.04 boots.

The problem started when I did a dist upgrade from 10.10. I restarted the computer only to get stuck on init running through all of its scripts. I was still able to alt+ctrl+F1 to get a terminal so I logged in and su'd to root and ran 'startx &' and got pushed directly into the GUI. everything works fine but when I restarted I had the same issue, I checked my xorg.conf and it looks fine, gdm is running although I have yet to see it and I can run 'startx &' to get the root desktop so I know that X is working it is just not getting started by init.

---

### Post by UCSBGauchosRock on 2011-07-21
> **dagamant said:**
> X11 does not start when ubuntu 11.04 boots.

The problem started when I did a dist upgrade from 10.10. I restarted the computer only to get stuck on init running through all of its scripts. I was still able to alt+ctrl+F1 to get a terminal so I logged in and su'd to root and ran 'startx &' and got pushed directly into the GUI. everything works fine but when I restarted I had the same issue, I checked my xorg.conf and it looks fine, gdm is running although I have yet to see it and I can run 'startx &' to get the root desktop so I know that X is working it is just not getting started by init.

I have noticed this is a problem with the newest kernel update. So if you are running the kernel in question, 2.6.38-11, you are going to have that problem.

My Solution: If you have not deleted the 2.6.38-10 kernel hold shift to enter GRUB during boot and select that kernel. If you have deleted it enter virtual terminal and run "sudo apt-get install linux-headers-2.6.38-10" without the quotes. 

To give a deeper explanation, when you did the distro upgrade from Maverick, this kernel was probably installed WITHOUT the 2.6.38-10 kernel so more than likely you will have to enter virtual terminal and install manually from there. 

Hope this helps.

---

### Post by dagamant on 2011-07-22
t

---

### Post by dagamant on 2011-07-22
> **UCSBGauchosRock said:**
> I have noticed this is a problem with the newest kernel update. So if you are running the kernel in question, 2.6.38-11, you are going to have that problem.

My Solution: If you have not deleted the 2.6.38-10 kernel hold shift to enter GRUB during boot and select that kernel. If you have deleted it enter virtual terminal and run "sudo apt-get install linux-headers-2.6.38-10" without the quotes. 

To give a deeper explanation, when you did the distro upgrade from Maverick, this kernel was probably installed WITHOUT the 2.6.38-10 kernel so more than likely you will have to enter virtual terminal and install manually from there. 

Hope this helps.

I thought it might be a problem with the newest kernel that was installed, I have the past 5 kernel updates that I have done so I tried switching to one of them (I think it was 2.6.38 or 2.6.35 but I dont have it in front of me right now) and still have the same problem. I am starting to think that Upstart is having an issue since I checked init.d and my boot log and everything looks OK.

---

