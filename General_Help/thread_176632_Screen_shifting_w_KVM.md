---
title: "Screen shifting w/ KVM"
date: 2006-05-15
forum: General Help
---

### Post by meznak on 2006-05-15
I am running ubuntu 5.10 with a geForce FX5500 and displaying thru a KVM (MiniView CS-102U).  On the other side of this KVM is a windoze box running a geForce 6600.  My problem is that I can't set my monitor (Mitsubishi Diamond Pro 900u) to center each of my displays.  I can either have the 'doze screen centered and the ubuntu screen shifted right ~.25" or I can have the ubuntu screen centered and the win screen left ~.25".  I have checked all of my configurations and everything looks okay to me.  I also have the latest 'doze drivers.  Where should I look from this point?  ](*,)

---

### Post by blackgibson on 2006-05-16
What I did was set the adjustments on the monitor itself for Windows. Under Ubuntu, I used xvidtune to adjust the settings for X. Just open a terminal and type

xvidtune


Hope that helps ya

---

### Post by meznak on 2006-05-20
That did the trick... nifty tool :)
Is there any way to make it change in smaller increments? or someplace I can change those numbers by hand?  It's almost exactly where I want it, but it still needs to move left about 2px

---

### Post by jeremytaylor on 2006-05-22
Use the show button in xvidtune to print out the modeline. Then just paste this into your xorg.conf in place of your current modeline. You can then play with the numbers manually if you so wish (and also you won't have to run xvidtune every time you reboot)
jeremy

---

