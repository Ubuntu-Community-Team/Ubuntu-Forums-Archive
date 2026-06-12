---
title: "Refresh rate problems"
date: 2009-12-16
forum: General Help
---

### Post by manuel777 on 2009-12-16
Hi, i installed ubuntu 9.10 on my compuuter yesterday, it all works perfectly, i downloaded and installed the nvidia drivers, but when i reseted to apply the changes i get a message from my monitor saying "Frecuency out of range: 81.1 khz / 65khz"
 Ubuntu loads perfectly, i just cant see anything because the frecuency the drivers cofigured does not addapt to my monitor. I can only acces to the terminals by pressing Ctrl+Alt+F1
I tried using the command 'nvidia-settings --assign=RefreshRate=75' but that didnt worked ( i get constant messages sayinf the display isnt defined )
any help please? :(

---

### Post by synapsys on 2009-12-16
Try this from command line:

```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot -n
```Then try adding recommended nvidia driver from System >> Administration >> Hardware Drivers

---

### Post by manuel777 on 2009-12-16
> **synapsys said:**
> 
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot -n
```

It doesnt seem to do anything... wasnt the xorg file removed in v9.10?

---

