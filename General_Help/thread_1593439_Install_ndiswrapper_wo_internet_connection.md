---
title: "Install ndiswrapper w/o internet connection?"
date: 2010-10-11
forum: General Help
---

### Post by coldfire6695 on 2010-10-11
So I have installed Ubuntu on my desktop, I have a wireless card that I know works w/ ndiswrapper and the INF/sys files I have, but I have no way of getting connecte to the internet (Ethernet requires and update) . So, My question is, Can I install Ndiswrapper w/o an internet connection (maybe put it on a CD or Flashdrive?).

---

### Post by Jaiichi on 2010-10-11
Yes you're able to, I had to do this as well. I believe you need these 3 files:

ndisgtk
ndiswrapper-common
ndiswrapper-utils

They're all .deb packages if my memory serves me correctly

---

### Post by coldfire6695 on 2010-10-11
I was looking around and was able to get it installed w/ the CD. But it says "Error: ndiswrapper-utils-1.9 not installed! "

---

### Post by coldfire6695 on 2010-10-11
Sorry to double post but..
 
I have got it working! 
 
-Download that packages from Ubuntu's archives
 
-Then put them on a flash drive and insert the ubuntu installation CD
 
-Install the deb packages as normal :D

---

