---
title: "Ubuntu crash during firefox"
date: 2010-09-03
forum: General Help
---

### Post by mrkiff on 2010-09-03
Hi all,

I'm fairly new to Ubuntu so please forgive me if this sounds daft, I've searched the forums alreads and had no luck.

I recently installed Ubuntu 10.04.1 onto an old machine. If I don't use it, it will stay on indefinatly. However when I start to use firefox for normal web browsing It caused a crash. Video can be found: [http://www.youtube.com/watch?v=f3pIgpYjviE](http://www.youtube.com/watch?v=f3pIgpYjviE)

The crash will loop until I press the power off button, at which point the ubuntu shutdown screen will be displayed.

Does anyone know what to do about this issue? 

Thanks in advance,

mrkiff

---

### Post by mrkiff on 2010-09-16
Nobody's got any ideas then?

---

### Post by TroN-0074 on 2010-09-16
Hi mrkiff. I had a similar problem and this is what I did.
>  Other graphics card users including nVidia may get a black screen with flashing cursor and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801")
One fix for this is to create this file.
    ```
 
     gksu gedit /etc/initramfs-tools/conf.d/splash 
``` and add this option FRAMEBUFFER=y, save the file.
Then
     ```

     sudo update-initramfs -u 
```Plymouth now has a hard dependency on mountall thus trying to  remove Plymouth would remove half the OS. The advice is, if you don't  want a graphical boot then uninstall any plymouth themes. I havent had the problem in two days now. Please let us know if it works for you.

---

### Post by blackness on 2010-10-29
Hey mrkiff.
did you get a chance to try TroN-0074's suggestion? did it work? New to Ubuntu. Actually I had for 2 weeks now & I'm having the same proplem (though it sometimes happen and sometimes it doesn't)
would apreciate a reply

---

