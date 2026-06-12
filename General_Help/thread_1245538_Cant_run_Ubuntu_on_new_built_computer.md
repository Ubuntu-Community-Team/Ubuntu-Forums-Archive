---
title: "Cant run Ubuntu on new built computer"
date: 2009-08-20
forum: General Help
---

### Post by crhatigan on 2009-08-20
I just put together my new computer and tried to run 8.10 on it and it would open the OS but as soon as it started to actually load the screen went black and then says "no signal." I have an ATI HD 3870 graphics card and a Gigabyte GA-MA790X-UD4P motherboard.  I think it has something to do with the video card drivers but I have no idea how to go about fixing it. Any help would be greatly appreciated.

---

### Post by ibutho on 2009-08-20
Hi and welcome to the forums. 

If you are having graphics problems, you could try installing Ubuntu using the alternate install cd and then configure the graphics later. Another option would be to try a newer version.

---

### Post by crhatigan on 2009-08-20
I got 9.04 on a cd and tried that and it did even worse it wouldnt run at all

---

### Post by crhatigan on 2009-08-20
what alternate install cd are you talking about

---

### Post by matthewbpt on 2009-08-20
The alternate cd is here [http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/) look lower down the page. The alternate cd is a text base installed that doesn't open a graphical UI during install, but it will boot to a normal graphical desktop after installation.

---

### Post by crhatigan on 2009-08-20
I am downloading it now but its taking some time.  After its installed should it run ok or will i have to put in some new drivers, any idea?

---

### Post by ibutho on 2009-08-20
> **crhatigan said:**
> I am downloading it now but its taking some time.  After its installed should it run ok or will i have to put in some new drivers, any idea?

I am not sure whether you will need additional drivers, but once you have installed from the alternate cd, you could use the fbdev or vesa drivers (this will give you a working gui but no 3d acceleration) whilst you try to fighure out which ATI drivers to use.

---

