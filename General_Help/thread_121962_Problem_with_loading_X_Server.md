---
title: "Problem with loading X Server"
date: 2006-01-26
forum: General Help
---

### Post by NightCircle on 2006-01-26
When I try the ubuntu Live CD, after a while when everything has loaded and I have selected Resolutions, Languages etc. an error occurs.
It says something similiar to:
Couldn't load your graphical interface X Server.
Do you want to see the error-log?
<Yes> <No>

I cant choose either Yes or No, it just moves on to the screen where I can input commands. No graphical interface, just plain black and white DOS-style.

I am trying on an IBM ThinkCentre.
I have tried on another computer before (Compaq Presario) and it worked fine without any errors at all there.

Looking forward for help!

---

### Post by christhemonkey on 2006-01-26
type into this prompt
sudo dpkg-reconfigure xserver-xorg
and select options that look apropriate!
If this doesnt help;
post the outcome of your error log file.

---

### Post by NightCircle on 2006-01-26
I tried typing the row you wrote and configured it, but I still get the same error.
I installed Ubuntu to my harddrive, but I get the same error there too.
I *can* use the non-graphical interface, but since I don't know more than about 5 Linux commands, it is quite pointless.

Maybe I should mention that I have a ATI X700Pro (PCI-E) as graphics-card.

---

### Post by liquidcourage1 on 2006-01-26
same problem.  I think it's the whole PCI-e thing.  I'm attempting to install on an AMD64 4000 w/ the 64bit distro.  How do we get the ATI drivers to load and recognize the PCI-e board?

---

### Post by mettallicat on 2006-01-26
try to down one version in your atidrivers and see if you have done weel the flgrconfig thing

---

### Post by liquidcourage1 on 2006-01-27
I can DL the ATI drivers but what command is that and how do I access that file?  Keep in mind I'll have to DL it from windows.  I guess I could put it on a disk, but can I access files from the command prompt of Ubuntu?

---

