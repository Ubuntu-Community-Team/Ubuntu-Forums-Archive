---
title: "Monitor loses signal/out of range"
date: 2011-03-01
forum: General Help
---

### Post by Xero1770 on 2011-03-01
Hello, I am running a dual boot system with Windows 7 and Ubuntu 10.10, both 64-bit. The problem is that whenever I try to start up Ubuntu, the monitor will lose signal. I have tried both my monitors, together and individually, the monitor (my newer one, an Acer 20") that I normally use loses signal alltogether and the monitor goes into standby, my other one which is an older Microtek c893 will come up with 'out of range' and also go into standby. I have tried reinstalling Ubuntu, aswell as multiple ctrl + alt keyhere commands, to no avail. I have also tried booting into recovery mode which also has the same result. 
I'll also add that the Live CD works perfectly fine, not sure why the installed one will not.

Operating System: Ubuntu 10.10
Monitor: Acer Technologies 20" (1680 x 1050 and 60Hz refresh rate)
Graphics Card: MSI 9600GT

Help would be much appreciated. :)

---

### Post by Xero1770 on 2011-03-01
Bump. Onboard video works fine, but with my 9600 which I would like to use does not. Any solutions?

---

### Post by Pernig on 2011-03-01
Since when did you have the problem? Did you recently apply updates?

The reason I ask this is I just did an update and the kernel it installed (2.6.35-27-generic) has broken my graphics too. I also am using a 9600 GT. I'm trying to find out more about the problem, I will report back when I know more.

If it turns out you are having the same problem as me, a temporary fix would be to boot from the older kernel. To do this, when you first switch on your computer there is a list of operating systems to choose from, don't pick Ubuntu, with linux 2.6.35-27-generic, but choose an older one instead. The older kernels are saved in the boot menu in case we ever run into issues like this.

Edit: If this isn't the problem you are having, try editing the options in the boot menu (I think you press ctrl+e, but it does say) and adding 'nomodeset' to the parameters.

---

### Post by Xero1770 on 2011-03-01
I'll give it a shot, will edit if it works. EDIT: no dice there. This is a fresh install and my first time working with ubuntu, the kernel is 2.6.35-22-generic.

---

### Post by Pernig on 2011-03-01
Long shot here, but try adding the following parameter on a new line in the boot options:

rdblacklist=nouveau

---

### Post by Xero1770 on 2011-03-02
Nope, didnt work. I'd rather not remove my gpu and use onboard everytime I want to use ubuntu. Any other suggestions?

---

### Post by Xero1770 on 2011-03-09
Bumpity bump bump. Still having this issue. Nobody has some form of insight?

---

### Post by Xero1770 on 2011-03-12
Bump again. Could really use help here.

---

