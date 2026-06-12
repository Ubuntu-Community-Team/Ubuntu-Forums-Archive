---
title: "Ubuntu's logo is to big after installing Nvidia drivers, how can i fix this?"
date: 2010-08-19
forum: General Help
---

### Post by Lukasz Tarkowski on 2010-08-19
Ubuntu's logo is to big after installing Nvidia drivers, how can i fix this?

---

### Post by Marcelo Ruiz on 2010-08-19
Its big and, in my case, has a weird flickering for 1 second...

---

### Post by Lukasz Tarkowski on 2010-08-19
hmm hope they can fix it, Never install nvidia Manually it messed up my Ubuntu, always use hardware drivers in System/Adminisration/Hardware Dribvers

---

### Post by Ginsu543 on 2010-08-19
Are you talking about the Plymouth screen which comes up with the Ubuntu logo and purple dots that light up underneath? If so, this is a known bug with nVidia graphics drivers with an easy workaround.

First, open Terminal. Then type:
```

sudo gedit /etc/default/grub

```Then, you want to add the following line:
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1920x1200
**GRUB_GFXPAYLOAD_LINUX=1920x1200** <-- set this to whatever your screen resolution is

```Reboot and see if your problem is fixed.

---

### Post by Lukasz Tarkowski on 2010-08-20
Thank you Ginsu543 it has worked ;)

---

