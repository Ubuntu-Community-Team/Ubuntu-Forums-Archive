---
title: "VirtualBox's Guest Additions - utility was not found"
date: 2011-07-26
forum: General Help
---

### Post by le1 on 2011-07-26
Hey there, 

If you're installing Linux Additions in VirtualBox (VBoxLinuxAdditions.run) and get:

"The make utility was not found. If the following module compilation fails then this could be the reason and you should try installing it.

The gcc utility was not found. If the following module compilation fails then this could be the reason and you should try installing it."

then go to synaptic and install "make" (An utility for Directing compilation) and gcc (The GNU C compiler) 
or use "sudo apt-get install make gcc"

and all should go well afterwards but if you'll still be missing something go to synaptic and see what would be installed if you choose virtualbox-guest-additions (guest additions iso image for VirtualBox) and match it with what you need.

---

### Post by scoualou on 2011-07-29
Hello,

I had the problem you mentionned when trying to install Guest additions for ubuntu 11.04. I checked that gcc and make are both installed and updated. But it doesn't change anything. Have you experienced something similar or do you know where it might be from?

Thank you 

Scoualou

---

### Post by le1 on 2011-07-30
Hey there,

Please paste the output info from terminal, let's see what's happening there...

---

