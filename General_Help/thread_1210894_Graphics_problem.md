---
title: "Graphics problem"
date: 2009-07-12
forum: General Help
---

### Post by Slinx on 2009-07-12
I'm having a problem with ubuntu 5.10 I know its old and theres better versions but I had the disc laying around and wanted to install it for now while I am waiting for my new cd to come in the mail and everything seemed to install good untill I noticed some weird electric fuzzy looking lines going verticle down my screeen and if I look close I notice some times that the screen seems kind of wavery and worst is that it doesnt show thigns for example if I go to tools and admististrative theres nothign presented untill I move the mouse over where it should be and sometimes things dont leave the screen after I close the application the image is just stuck there untill I drag something over it and erase it. In terminal its the same too i have to highlight everythign to display the changes made. I'm not sure what I need to do to fix this since i was told by some one it sounds like a graphics card problem to install something like nvidia drivers but my graphics is onboard and I beleive its SiS mirage1.
 oh and its the same on the live cd too.
Thanks to anyone who can help me out.
ps I am new to linux.

---

### Post by fragos on 2009-07-12
I can't remember having problems like you describe and I've used every version starting with 5.10. There is an SIS driver which I believe was part of your install. Look at /etc/X11/xorg.conf and see what driver is called out for your system. I seem to remember setting Driver to "sis". Save a backup of xorg if you edit it. You'll need root privledges to edit xorg.conf. Open a terminal window and run "gksudo gedit /etc/X11/xorg.conf". Enter your own own password when requested. When you get 9.04 you'll be very pleased with improvements.

---

