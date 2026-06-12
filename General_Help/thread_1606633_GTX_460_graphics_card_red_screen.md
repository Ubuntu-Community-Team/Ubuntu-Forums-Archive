---
title: "GTX 460 graphics card red screen"
date: 2010-10-26
forum: General Help
---

### Post by henners91 on 2010-10-26
Hi, relatively new user. I've just installed ubuntu 10.10 on my desktop system. it worked fine with my 5770 but when using my gtx 460 it has a crashing problem. After roughly 30 secs running the screen has a red cast and a grid pattern to the bottom right of the mouse. Need directions to solve this such as new drivers or an exact sequence etc as i've only got 30 secs to complete the process before it freezes. Specific graphics card is a gainward gtx 460 GLH too btw.
 Thanks for any help given.

---

### Post by LowSky on 2010-10-26
boot into recovery mode. 

then install the nvidia drivers

```
sudo apt-get install nvidia-current
```
reboot
then run 
```
sudo nvidia-xconfig
```
reboot and all should work

---

### Post by henners91 on 2010-10-27
Great i'll give that a try after uni. I've tried turning off propietary drivers but that didn't help. then tried updating but obviously that's with the desktop loaded so it just crashes. Will reply if this works, thanks for the help.

---

### Post by henners91 on 2010-10-27
Hey. That stopped it from crashing but put it in 800x600 and wouldn't let me go any higher. I updated my ubuntu install and this didn't change still so i downloaded and re-installed the new drivers for my 460 it's still doing the red cast as it crashes like before. Any other solutions to try?
 Thanks in advance.

---

### Post by Abadaar on 2010-12-02
Hello. I think I might have had the same problem as you earlier. It is related to the BIOS of the graphics card. I had to update the graphics card BIOS before I could use the newer nvidia drivers reliably.

Select your card, download BIOS update, apply in Windows.
[http://www.gainward.com/main/vgapc.php?vgapc_id=25&lang=en]("http://www.gainward.com/main/vgapc.php?vgapc_id=25&lang=en")

---

