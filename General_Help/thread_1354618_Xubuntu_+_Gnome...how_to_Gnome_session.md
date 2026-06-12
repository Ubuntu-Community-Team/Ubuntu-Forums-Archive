---
title: "Xubuntu + Gnome...how to Gnome session"
date: 2009-12-14
forum: General Help
---

### Post by jeffsa12 on 2009-12-14
I'm setting up a computer for my 7yo daughter, an Acer Aspire Revo.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883103228&cm_re=revo-_-83-103-228-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16883103228&cm_re=revo-_-83-103-228-_-Product)

Windows will be removed and replaced with a customized Linux install. 

The computer should be here in a few days. I've been playing with Qimo and KIDOZ in VBox to check it out and prepare for the real install. Qimo is a Xubuntu based distro for kids and KIDOZ is kind of a very locked down web browser for kids.

I prefer the Gnome desktop on all my Linux installs, and Qimo is Xfce only. Without getting a debate started in the process of getting some help, 
**I'd like to know, once I've installed ubuntu-desktop on Xubuntu, how to log into a Gnome session.** 
I don't have the option to "choose sessions" upon login as I have in the past when I installing KDE on Ubuntu.

---

### Post by ankspo71 on 2009-12-14
Hi,

Since you are testing it out in vbox, are you able to see which display manager it is using by searching in Synaptic Package Manager or a similar package management program? I'm only guessing, but I would immagine the display manager might be XDM or something smaller. Since the distro is based on Xubuntu, you shouldn't have problems replacing XDM (or another display manager) with GDM or KDM, one of which is more familiar to you. In synaptic, the previous display manager probably will be automatically selected to be removed when the new one is selected to be installed. 

From there you could go on to install your favorite desktop

Do this type of testing in virtualbox though, because it only takes but a second to make a backup of your virtualbox folder for in case you need a re-install. 

Hope this helps.
James

---

### Post by ankspo71 on 2009-12-14
Oh and by the way, the newest GDM (ubuntu 9.10 and newer) requires you to click on the username in the "log in window" (the display manager window), before it will provide you a way to log into the gnome session.

So if GDM is used, log out of the xfce session, click on the desired username, then look down at the bottom of the screen for the desired session, choose gnome, then go back and enter your password and log in.

---

### Post by jeffsa12 on 2009-12-14
It's based on Xubuntu 8.10. GDM is installed, but Qimo log in screen has only restart and shutdown options.

---

