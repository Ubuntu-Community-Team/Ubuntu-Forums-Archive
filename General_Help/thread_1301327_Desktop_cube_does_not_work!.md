---
title: "Desktop cube does not work!"
date: 2009-10-25
forum: General Help
---

### Post by meinvateristnein on 2009-10-25
any suggestions? i am running 8.10 and have an ati card

---

### Post by undecim on 2009-10-26
Have you enabled the "Desktop Cube" and "Rotate Cube" plugins in Compiz?

EDIT: And also, check your drivers (System -> Administration -> Hardware Drivers)

What card model do you have? In a terminal, type "lspci | grep VGA" to find out

---

### Post by dbyjazz on 2009-10-26
and do you have Desktop Effects turned on?

---

### Post by misfitpierce on 2009-10-26
TERMINAL : sudo apt-get install compizconfig-settings-manager
if you have not done so already in order to turn on 3d cube and rotate cube as said above once effects are on.

---

### Post by meinvateristnein on 2009-10-26
yes i have enabled all of that even before i posted ... and the ouput of lscpi is 
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

BTw i am not a total noob at this so i know the basics

---

### Post by scouser73 on 2009-10-26
Here is a tutorial for enabling the CompizConfig cube: [[COLOR="Red"]**Compiz Config Tutorial**[/COLOR]]("http://www.ghacks.net/2009/07/30/configuring-the-appearance-of-the-compiz-cube/comment-page-1/#comment-859972/")

---

### Post by evan79 on 2009-11-02
hi i also cant get the desktop cube to work, the output for command

01:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)

i followed the links instructions, all except the cube top, i could not find that tab/section?

---

### Post by jualin on 2009-11-02
> **evan79 said:**
> hi i also cant get the desktop cube to work, the output for command

01:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)

i followed the links instructions, all except the cube top, i could not find that tab/section?

Do other effects work? Have you enabled visual effects under System, Administration, Appearance?

---

### Post by mavros on 2009-11-02
I have been playing around and finally made it work for Intel and Nivdia cards. Have you tried?

[LIST]
[*]unchecking under Effects -> 3D Windows  ->  Rotate on Mouse only
[*]experimenting with Cube reflection and deformation also under Effects, I use a Cylinder now but once you make the cylinder work you can go back to a pure cube
[/LIST]
You also need a minimum number of desktops/working spaces 6 works. WH\hen I had less the desktops flip but don't form a cube

---

### Post by lucianct on 2009-11-08
i can't enable desktop cube in karmic either. i have an ati radeon hd4200 with the proprietary drivers. everything works, except cube

---

