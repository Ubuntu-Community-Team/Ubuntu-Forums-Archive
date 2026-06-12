---
title: "reboot after installation - blank screen"
date: 2010-02-08
forum: General Help
---

### Post by adeelmahmood on 2010-02-08
after installing ubuntu 9.10 (karmic) .. it continues to work fine until I restart it .. once i restart all i get is the wheel kind of loading image and then the screen goes black .. with no mouse no keyboard nothing .. 

i can only restart (by resetting the power button) and log back in the recovery mode to get to the terminal .. after looking at some of the messages posted here it seems like some resolution compatibilty issue .. i have a 1920x1200 resolution monitor .. 

so how can i get the graphical interface back up .. also is there a way to install ubnutu with the graphical interface completely turned off .. i am really actually able to get everything done from the terminal anyways so I dont really need to gui .. it seems like that might help solve my problem too ..

please comment .. any help is appreciated

---

### Post by darolu on 2010-02-08
Try reconfiguring your xorg.conf file, first create a back-up file of it (better safe than sorry):
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Then reconfigure with:
```
sudo dpkg-reconfigure xserver-xorg
```
I had a similar problem few months ago when I changed my monitor, I fixed it following this steps, hopefully it will work for you too.

I think you can install Ubuntu with no GUI using the Alternate CD.

---

