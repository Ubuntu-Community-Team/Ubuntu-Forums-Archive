---
title: "Help to install nvidia drivers with apt-get!"
date: 2006-04-25
forum: General Help
---

### Post by Dasf on 2006-04-25
What source list do I need to install nvidia-settings? I run on Kubuntu and because it doesn't have the usual source list to apt-get added... I also want a source list that I can install tcltls, libssl, mplayer and a relative new amsnversion. I think all who have ubuntu already have this program availible with apt-get? But I dont have it and now want it.

---

### Post by Qrk on 2006-04-25
Kubuntu uses the same sources as Ubuntu. 

You probably haven't enabled universe and multiverse.

You can do that by 

```
sudo kwrite /etc/apt/sources.list
```

Remove the # in front of the lines with links.

---

### Post by rykel on 2006-04-25
[QUOTE=Dasf]What source list do I need to install nvidia-settings? I run on Kubuntu and because it doesn't have the usual source list to apt-get added... I also want a source list that I can install tcltls, libssl, mplayer and a relative new amsnversion. I think all who have ubuntu already have this program availible with apt-get? But I dont have it and now want it.[/QUOTE]

hi, doesnt kubuntu use the same repositories as ubuntu?   :rolleyes: 

anywae, try this (it is the way it works in ubuntu):

1.   launch Synaptic package manager
2.   select Settings / Repositories
3.   ADD all the Universe and Multiverse for "dapper drake", "security updates", "updates" and "Backports"
4.   RELOAD (yeah, tis is NOT an automatic process... u have to press the button after u change ur repositories)
5.   install watever programs u want (eg. nvidia-glx to get nvidia-settings ~ they are now one single program)
6.   in a terminal, type **nvidia-glx-config enable**
7.   LOG OUT / reboot
8.   in a terminal, type **nvidia-settings**

tat should get u nvidia-settings... as for mplayer etc. play around wif them, u shld get something out soon...   :KS

---

