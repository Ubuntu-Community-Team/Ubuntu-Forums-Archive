---
title: "Monitor Unknown Intel Graphics"
date: 2011-01-27
forum: General Help
---

### Post by Aydos on 2011-01-27
Hello. I just installed Ubuntu 10.10 on my Dell Latitude D430 that I use at work. I have it on my desk docked going to a Dell LCD Monitor. When I go into the monitor set up it says Unknown for the monitor and Laptop for the actual laptop display. Also, I have very low resolutions for the "Unknown" monitor.

I am trying to resolved this issue so that I have better resolutions on the external monitor and then I can try to extend the desktop between 2 screens.

I found something online about adding the intel PPA and I did that, but now what. There is no xorg.conf that I can find for 10.10. 

I have not used Linux in a while so be gentle with me. I work for the IT dept at a private school and would love to get this situated and get back to work lol.

Thank you in advance.

---

### Post by Kirboosy on 2011-01-27
Well I guess I will be the first person to take a stab at it.

First off, have you updated the system? (System-->Admin-->Update Manager)

Also, check for a video driver (System --> Admin-->Additional Drivers) If nothing comes up then don't sweat it.

Can you adjust the resolution of either monitor when you have the two screens displaying?

---

### Post by Aydos on 2011-01-27
Thank you for being the first one to step in line.

Yes I have already completely done and update and the only thing that has shown up in the additional drivers is my wireless card which I have updated.

The laptop display has all of the resolutions and looks wonderful.

The Dell external LCD monitor has low resolutions and everything is stretched and blurred.

---

### Post by Kirboosy on 2011-01-27
You should be able to change the monitor resolution still under the Monitor settings. I know when I hook my Dell Laptop up to my monitor it says "Unknown Monitor" but I can still change it.

Click on the Unknown screen and try to adjust the resolution.

---

### Post by Aydos on 2011-01-27
It will let me adjust it it just only has 3 small resolutions and the biggest one is stretched b/c it is so small.

---

### Post by Kirboosy on 2011-01-27
What is the exact Intel Graphics chipset?

---

### Post by Aydos on 2011-01-27
Intel GMA 950

---

### Post by Kirboosy on 2011-01-27
[This might prove helpful]("https://wiki.ubuntu.com/X/Config/Resolution#How%20to%20setup%20a%20dual%20monitor")

IF that doesn't work you can try downloading and installing a driver from Intel's website.

---

