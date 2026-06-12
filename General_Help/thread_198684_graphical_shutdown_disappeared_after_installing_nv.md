---
title: "graphical shutdown disappeared after installing nvidia drivers"
date: 2006-06-17
forum: General Help
---

### Post by zeus77 on 2006-06-17
The graphical shutdown disappeared after installing nvidia drivers... now it's just a blank screen.  I still have graphical startup, and everything else works fine.  Not a big deal, but it would be nice to fix.

Anyone else seen this?  Any ideas?

---

### Post by tseliot on 2006-06-19
Try point 13 of the Problems Section of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")

---

### Post by daedalusman on 2006-06-19
[QUOTE=tseliot]Try point 13 of the Problems Section of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")[/QUOTE]


I'm expericencing the same problem, I took a look that link and did what it says, but my vitrual terms are still messed up. I followed your guide to install the lastest nvidia drivers. I had the same problem with the nvidia-glx package, which is why I went to the nvidia binary. The nvidia binary also seemed to have messed up my xgl-compiz session, though I'm still looking into that one. Anyways I would like to get my vitrual terminals working again just in case I actually come across a need to use them, such as updating the nvidia driver. To see what it is doing check out the picture I took of my screen (attached). Can anyone tell me how to go about fixing this, thanks?

---

### Post by tseliot on 2006-06-20
[QUOTE=daedalusman]I'm expericencing the same problem, I took a look that link and did what it says, but my vitrual terms are still messed up. I followed your guide to install the lastest nvidia drivers. I had the same problem with the nvidia-glx package, which is why I went to the nvidia binary. The nvidia binary also seemed to have messed up my xgl-compiz session, though I'm still looking into that one. Anyways I would like to get my vitrual terminals working again just in case I actually come across a need to use them, such as updating the nvidia driver. To see what it is doing check out the picture I took of my screen (attached). Can anyone tell me how to go about fixing this, thanks?[/QUOTE]
Remove XGL. It's not stable enough.

---

### Post by daedalusman on 2006-06-20
[QUOTE=tseliot]Remove XGL. It's not stable enough.[/QUOTE]

I don't see how that will fix my terminal issue. I run XGL as a serperate sesion (nested XGL) so not having it work isn't really causing any problems because its not even running at the moment and I'm still having the trouble with the terminals. Thanks for the reply though.

---

### Post by daedalusman on 2006-09-23
So has anyone figured out how to fix this issue with the vitrual terminals not displaying correctly. I just got my computer back online after about 3months of it being dead and updated the nvidia drivers to 8774 and my terminals still don't work, I just get a blank screen or a blank screen with green boxes scattered about. Can some shed some light on this issue, thanks.

---

