---
title: "3D performance"
date: 2010-08-10
forum: General Help
---

### Post by capsaicin on 2010-08-10
Hi,
My ubuntu cd (10.4 LTS) has just came today and i installed it first time.
My system is:

Asus P5KPL Mainboard
1 gb ram
Intel dual core 2.4
and the problem = Ati Radeon x1300/x1550 series graphics card.

I installed playonlinux and wine 1.1.42
I installed shaiya on playonlinux and updated.
When the game opens at 800x600 16 bit lowest resolution (or tries to open) it lags a lot, never make a perfect graphic. 
When i open the brutal chess, it lags too.
My glxgear points are over 5000 .
When i open the grand theft auto vice city, it dont lag so much but i see no models.

I installed official ati x 1xxxx linux drivers (i ran .run file in terminal.)
I dont have a xorg.conf file
I dont have a etc/shared/ati folder
Hardware drivers shows no driver.
Working of desktop applications is good.
How can i make playable shaiya on ubuntu?
I am searching for this for more than six hours.
I founded a new problem : sounds in macromedia flash comes with a one second latency

Thanks.

---

### Post by sandyd on 2010-08-10
> **capsaicin said:**
> Hi,
My ubuntu cd (10.4 LTS) has just came today and i installed it first time.
My system is:

Asus P5KPL Mainboard
1 gb ram
Intel dual core 2.4
and the problem = **Ati Radeon x1300/x1550 series graphics card.**

I installed playonlinux and wine 1.1.42
I installed shaiya on playonlinux and updated.
When the game opens at 800x600 16 bit lowest resolution (or tries to open) it lags a lot, never make a perfect graphic. 
When i open the brutal chess, it lags too.
My glxgear points are over 5000 .
When i open the grand theft auto vice city, it dont lag so much but i see no models.

I installed official ati x 1xxxx linux drivers (i ran .run file in terminal.)
I dont have a xorg.conf file
I dont have a etc/shared/ati folder
Hardware drivers shows no driver.
Working of desktop applications is good.
How can i make playable shaiya on ubuntu?
I am searching for this for more than six hours.

Thanks.
problem bolded. Tne drivers you downloaded do not support XOrg 7.5, which is the current version used in ubuntu.

---

### Post by capsaicin on 2010-08-10
And what should i do, thanks for reply, and please help me.

---

### Post by sandyd on 2010-08-10
> **capsaicin said:**
> And what should i do, thanks for reply, and please help me.
if you can run
```

glxgears
```
in the terminal without issues, your already using the best drivers.

---

### Post by capsaicin on 2010-08-10
So why i cant play games in 3d ?

---

### Post by sandyd on 2010-08-10
> **capsaicin said:**
> So why i cant play games in 3d ?
thats because your using the open-source radeon drivers, which are the only drivers to support your card.

---

### Post by capsaicin on 2010-08-10
At the end, i cant play shaiya in ubuntu i think and have to install xp again :(

---

