---
title: "Ubuntu Software Center untrusted"
date: 2011-02-16
forum: General Help
---

### Post by ~Middle on 2011-02-16
So the other day i had a major melt donw, and decided to re-install Ubuntu because it was very messed up.

But i am still getting a similar problem, when i try to install a program from USC, i get teh follwoing message (This is using gimp as an example):

> Requires installation of untrusted packages

The action would require the installation of packages from unauthenticated sources.

gimp gimp-data libbabl-0.0-0 libgegl-0.0-0 libgimp2.0 libhal1 libilmbase6 libopenexr6

I can install it by doing 

sudo apt-get gimp gimp-data libbabl-0.0-0 libgegl-0.0-0 libgimp2.0 libhal1 libilmbase6 libopenexr6

And saying yes to the source, however this shouldn't happen, and i worry about messing my system up again. 

Can anyone suggest an fix?

Thanks

---

### Post by 3Miro on 2011-02-16
If you have trouble installing things, you can check Synaptic Package Manager for what is "trusted" and "untrusted". You can also use aptitude from the command line, it is more sophisticated than apt-get when it comes to catching problems. That is about all that I know.

---

### Post by oldos2er on 2011-02-16
Try running ```
sudo apt-get update
```
If that doesn't work, see [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

### Post by ~Middle on 2011-02-16
Thanks for your reply

apt-get update did indeed fix the USC issue, i installed GIMP and ran an update from the update manager

However, half way through the update, it froze, and when i reboot, i just get a blank screen

I have got into a root shell, so what can i do??!!

Thanks alot

PS: remember that i installed this yesterday, so it is a clean install of Ubuntu 10.10!

---

