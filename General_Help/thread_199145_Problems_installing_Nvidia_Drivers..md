---
title: "Problems installing Nvidia Drivers."
date: 2006-06-18
forum: General Help
---

### Post by Skitatic on 2006-06-18
Hey guys,

Being very new to Linux I am trying to install my Nvidia graphics card.  I have download the supposed drivers the file called NVIDIA-Linux-x86-1.0-8762-pkg1.run but I am having some problems with then installing it.  

Can anyone please help me?  I have no idea what to do from here.

Thanks,
Skitatic.

---

### Post by jon_gunnar on 2006-06-18
[QUOTE=Skitatic]Hey guys,

Being very new to Linux I am trying to install my Nvidia graphics card.  I have download the supposed drivers the file called NVIDIA-Linux-x86-1.0-8762-pkg1.run but I am having some problems with then installing it.  

Can anyone please help me?  I have no idea what to do from here.

Thanks,
Skitatic.[/QUOTE]

Why not simply install it from apt or synaptic?
A simple search in synaptic for nvidia will give you what you want.Or apt-get

---

### Post by tseliot on 2006-06-18
Try this guide of mine:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

### Post by Skitatic on 2006-06-18
[QUOTE=jon_gunnar]Why not simply install it from apt or synaptic?
A simple search in synaptic for nvidia will give you what you want.Or apt-get[/QUOTE]

Do you have any idea what the terminal command for installing nvidia drivers is?

---

### Post by RAOF on 2006-06-18
[QUOTE=Skitatic]Do you have any idea what the terminal command for installing nvidia drivers is?[/QUOTE]
```
sudo aptitude install nvidia-glx
sudo nvidia-xconfig

```

---

### Post by tseliot on 2006-06-20
[QUOTE=Skitatic]Do you have any idea what the terminal command for installing nvidia drivers is?[/QUOTE]
See method 1 of my guide

---

