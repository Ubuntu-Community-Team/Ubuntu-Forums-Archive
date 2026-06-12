---
title: "Grub2 not displaying"
date: 2011-07-06
forum: General Help
---

### Post by graphius on 2011-07-06
An "obvious" fix if you can't see your grub2 menu while trying to dual boot.
I followed all the directions I could find and I still could not see my grub2 menu and so could not boot into windows (on the rare chance I needed to..).
The problem was that it was using a display resolution my monitor could not recognize...

edit the grub file
```
sudo gedit /etc/default/grub
```

Find the section that looks like this
> # The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
uncomment the line and change the resolution to your monitors native resolution. for me it looked like this
> # The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024
save and then run
```
sudo update-grub
```

Reboot and you should be able to see your menu.
If not, you can change the line
```
GRUB_HIDDEN_TIMEOUT_QUIET=true
```
to
```
GRUB_HIDDEN_TIMEOUT_QUIET=false
```

Don't forget to run
```
sudo update-grub
```

Hopefully this helps someone else as frustrated and braindead as me...:D

---

