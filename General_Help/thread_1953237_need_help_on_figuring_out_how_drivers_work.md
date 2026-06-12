---
title: "need help on figuring out how drivers work"
date: 2012-04-05
forum: General Help
---

### Post by milkyky on 2012-04-05
Hi i'm using Ubuntu 11.10 kernel 3.0.17.

I started to switch from windows to linux. My ubuntu works so far so good. Then when i start to play around with the drivers this question pop out. I dont really know how actually drivers works on linux coz compare to windows sys i just have to download and install the drivers and actually i dont know what actually happen.

I installed my ubuntu in an external hardisk. So i'll boot my usb hardisk everytime i want to use it. My current laptop has an nvidia graphic card and i also installed the driver for it thru the driver manager.

Now the question is, if i boot my external hardisk by using my frien's laptop which have different hardware, how can i solve the drivers part?:confused:

Any books that are related to how actually drivers and kernels works which can be recommended? I have some basic hardware programming knowledge on microcontroller. And i plan to work on more advanced system for my selfstudy.

Any guru can help or guide me on this?:confused:

thank you.

---

### Post by 3rdalbum on 2012-04-06
In theory, when you start Ubuntu on the friend's laptop it will bring up a warning that says "Ubuntu is running in low graphics mode" and you can choose to start the desktop in unaccelerated 2D or to redetect the hardware and start the desktop using open-source drivers. The latter is what you want.

In practice, I wouldn't risk my life on this happening reliably. It's worked for me before, but the procedure results in X having to restart. Sometimes, when X goes down, it simply won't come back up...

If possible I'd suggest just sticking with the open-source Nvidia driver and this way the hardware will be detected every time on boot. It should work properly every time you try it.

---

### Post by Herman on 2012-04-06
It's possible to fix a black screen by rebooting and choosing recovery mode, there are some options in there for resetting the graphics back to defaults if we had a video card driver installed for some other machine.

Another way to do it is simply to delete the /etc/X11/xorg.conf file in the portable USB installation by using some other Ubuntu such as a Live CD or whatever. 
Don't worry, Ubuntu will automatically generate a new one for you, but without your special driver and without any special settings you may have made. If you want to keep those, you might consider copying the file to a backup location or renaming it instead of deleting it.

Once you have Ubuntu up and running with the Xserver working again then you can choose whether or not to bother installing the driver for the other machine's video card. After all, it's free, and once you've run through this kind of procedure a couple of times it won't seem like any problem at all.

There's a message telling you to reboot after configuring your graphics. I usually just log out and log back in again rather than rebooting.

---

