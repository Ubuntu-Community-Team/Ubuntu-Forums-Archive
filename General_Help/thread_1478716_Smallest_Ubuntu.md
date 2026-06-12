---
title: "Smallest Ubuntu ?"
date: 2010-05-10
forum: General Help
---

### Post by mech7 on 2010-05-10
I installed Ubuntu JEOS 10.05 in virtual box but it still take around 230 MB When I create an appliance.. is there anyway to make it even smaller ?

---

### Post by mb_webguy on 2010-05-10
The smallest official variant of Ubuntu is Xubuntu, using the xfce desktop environment.  I don't know how big the final installation size is, but you need 192MB of memory to run the LiveCD, so I'd think the actual installation size would similarly be less than 230MB.

The actual "smallest Ubuntu" would be one using the [minimal installation disc]("https://help.ubuntu.com/community/Installation/MinimalCD").  The minimal installation CD image is less than 15MB, and results in a bare-bones installation of linux -- as no apps and no graphical desktop environment. If you want a graphical interface, you could install a lightweight window manager like Fluxbox.  Then you could install only those specific apps you need.  Doing this rather than trying to take some pre-packaged version and pare it down to the size you need, you should be able to create something reasonably usable at quite a bit less than that 230MB figure.

---

### Post by mech7 on 2010-05-10
> **mb_webguy said:**
> The smallest official variant of Ubuntu is Xubuntu, using the xfce desktop environment.  I don't know how big the final installation size is, but you need 192MB of memory to run the LiveCD, so I'd think the actual installation size would similarly be less than 230MB.

The actual "smallest Ubuntu" would be one using the [minimal installation disc]("https://help.ubuntu.com/community/Installation/MinimalCD").  The minimal installation CD image is less than 15MB, and results in a bare-bones installation of linux -- as no apps and no graphical desktop environment. If you want a graphical interface, you could install a lightweight window manager like Fluxbox.  Then you could install only those specific apps you need.  Doing this rather than trying to take some pre-packaged version and pare it down to the size you need, you should be able to create something reasonably usable at quite a bit less than that 230MB figure.

But my install comes from the VM Minimal install ? It it that big a difference between VM and Minimal install ? Or does virtual box add some stuff in a appliance ?

As I just installed a LAMP server and Samba

---

### Post by mech7 on 2010-05-10
I just installed the minimal install (from ubuntu cd) And it is still around 240 MB... only things installed where samba + lamp + open ssh server...
:confused:

---

### Post by melkespreng on 2010-05-10
The netbook versions like jolicloud or netbook remix.

But the smallest desktop ubuntu must be Lubuntu, or it's smaller than xubuntu I think.

---

### Post by 3rdalbum on 2010-05-10
I think anything smaller than JeOS (Just Enough Operating System) would be NeOS - (Not Enough Operating System).

---

### Post by mech7 on 2010-05-10
> **3rdalbum said:**
> I think anything smaller than JeOS (Just Enough Operating System) would be NeOS - (Not Enough Operating System).

Lol I see... but i see some appliances very very small like 15 mb... I just need to run apache & mysql & samba.. and would prefer ubuntu if the need comes up for some other software.. guess 230 mb will have to do :)

---

### Post by lykwydchykyn on 2010-05-10
> **mech7 said:**
> Lol I see... but i see some appliances very very small like 15 mb... I just need to run apache & mysql & samba.. and would prefer ubuntu if the need comes up for some other software.. guess 230 mb will have to do :)

I don't think there's a way to make Ubuntu any smaller, unless you just start deleting stuff.  

If you want to get in the 15 Mb range you need to look at something like tinycore.

---

