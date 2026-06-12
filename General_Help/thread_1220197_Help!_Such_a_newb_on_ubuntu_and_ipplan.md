---
title: "Help! Such a newb on ubuntu and ipplan"
date: 2009-07-22
forum: General Help
---

### Post by newbieaura on 2009-07-22
I am trying to find ways to do IP management and came across IPplan. Try to do it in windows and was tired messing with it in that OS. 

I want to use in Ubuntu. As a newb to linux this OS looks easy to use.

I have install Apache2, and Php, and mysql. But when I install the ipplan package all seem fine. I can not seem to access it. I am getting frustrate with it. I even try to manually to configure but I believe the install.php i believe doesnt mesh with the sudo command.](*,)

Can someone provide help on this or step by step instruction? To all that reply thank you in advance for your help.:-D

Aura

---

### Post by Tman5293 on 2009-07-22
Try this command in the terminal:

sudo ipplan

or it might be this:

sudo ip-plan

Good Luck!!! :guitar:

---

### Post by newbieaura on 2009-07-22
Try both command it said command not found in the terminal window.

Thanks though.

---

### Post by jdawiz on 2009-07-24
So, IPPlan is not a command it is accessed using a web browser.  What happens if you put this [http://localhost/ipplan](http://localhost/ipplan)   in your web browser address bar.  

The config files for ipplan are usually in /etc/ipplan directory.  The php and other files are in /usr/share/ipplan (on Ubuntu anyway).  Hope this helps.

---

