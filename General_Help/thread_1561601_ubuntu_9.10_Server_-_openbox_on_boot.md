---
title: "ubuntu 9.10 Server - openbox on boot?"
date: 2010-08-26
forum: General Help
---

### Post by LuniTux on 2010-08-26
Hello,

I'm sure there is probably an easy answer to this... I want to be able to have openbox load when I start my computer.

Something like:

```
username: xyz
password: xxxxxxxx

(start openbox here)
```

If it is easier to include a login screen with it, that would work as well. I also would like wbar to be able to start when openbox loads. any ideas?

Thanks in advance

---

### Post by LuniTux on 2010-08-28
I figured out the first part.

```
sudo apt-get install openbox gdm xorg
```

Next problem:

I have a signin screen, but when I sign in, openbox does not load. I get a blank desktop with a terminal emulator in the top left corner... How do I start openbox from here?

---

### Post by LuniTux on 2010-08-28
got it!

sudo apt-get -y install wdm xorg openbox

and openbox can be replaced with the following:

openbox
blackbox
fluxbox
lxde
xfce4

Others may work but i have not tested them

---

### Post by MooPi on 2010-08-28
Try at the prompt```
startx
```

---

### Post by LuniTux on 2010-09-01
i'm try to avoid having to type "startx" can that be done without xdm,wdg,gdm,kdm,slim, etc.?

---

### Post by LuniTux on 2010-09-10
Solutions I have found.

```
sudo apt-get install openbox xorg xdm** 
```

*xdm can be replaced with one of the following

xdm wdm gdm slim**

I probably missed a few but these seem to work.

**I could not install slim via "sudo apt-get install slim" but I installed it this way.

```
cd /tmp

wget http://mirrors.kernel.org/ubuntu/pool/universe/s/slim/slim_1.3.0-2_i386.deb

sudo dpkg -i slim_1.3.0-2_i386.deb

rm slim_1.3.0-2_i386.deb

sudo apt-get install -f
```

---

