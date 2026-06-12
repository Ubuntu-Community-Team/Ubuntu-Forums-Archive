---
title: "Nvidia driver logout issue"
date: 2011-12-01
forum: General Help
---

### Post by InfinitySquared on 2011-12-01
Greetings,
I just recently moved to Ubuntu and I'm lovin it so far. However I have run into a problem I do not know how to solve.
Whenever I try to logout , the screen turns black and I can't do anything.
I already reinstalled Ubuntu a couple of times thinking it has something to do with the installation, but turns out it's the Nvidia driver. I know this, because if I remove the driver everything works flawlessly. I installed the driver that came up on Additional Drivers.
This also happens if I go to the terminal and shut down the login manager and then start it up again.(sudo stop lightdm -> sudo start lightdm). The screen just stays blank forever and my keyboard takes no input.
I'm using Ubuntu 11.10 and the lightdm desktop manager.
I'm looking forward to your reply,
Yours faithfully,
Infinity Squared



EDIT: I forgot to mention, my graphics card is Nvidia Geforce GTS 450

---

### Post by InfinitySquared on 2011-12-02
Bump.
Help please!

---

### Post by efflandt on 2011-12-02
Are you sure you are giving it enough time for Linux to shutdown after the screen goes dark?  I seem to have a shutdown delay due to modem manager failing to stop (I don't use a modem, so not sure if it is even running).

The whole Unity/compiz thing can work a video card harder, which may make any issues more noticeable.  Apparently my GT 430 (Galaxie brand) was failing because after a year it began freezing in Win7 and 11.10, even though it usually still worked fine in 10.10 (all 64-bit).  Yet even with most recent x-swat driver 290.10, which usually worked fine in Maverick, I could not hardly boot 11.10 without losing video signal between grub menu and login, or screen freeze ups in X (everything booted from 11.10's grub on sdb).  And if I went to the console in 11.10 there was no getting back to X (Alt+F7 would lose video signal entirely) and **sudo service lightdm stop** would corrupt the screen.

So I replaced my video card with EVGA GTX 550 Ti (which uses more power, but has separate power connection) and 11.10 has worked fine.  Using x-swat 290.10 drivers, returning from console to X (Alt+F7) takes about 10 seconds.  No boot issues or freezes so far.  Waking from suspend seems to take a full minute (cold booting from SSD is much faster).

If you want to try newer x-swat nvidia drivers, just do:```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```Then using **Update Manager** to **Check** and then install updates.

---

### Post by InfinitySquared on 2011-12-05
I did like you said, but it already made it worse and I still can't logout.

---

### Post by InfinitySquared on 2011-12-05
I've read that you can add a line to the GDM config file to make it terminate the server, but I'm using LightDM. So if anyone has any idea how to do it on LightDM, please reply

---

### Post by InfinitySquared on 2011-12-05
Bump
Help please!

---

### Post by InfinitySquared on 2011-12-06
I installed the driver from Nvidia's website but then ubuntu wouldn't start so I had to reinstall it.

---

### Post by InfinitySquared on 2011-12-08
I'm about to give up. Please, someone...

---

