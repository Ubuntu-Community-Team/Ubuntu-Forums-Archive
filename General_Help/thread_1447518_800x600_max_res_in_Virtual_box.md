---
title: "800x600 max res in Virtual box"
date: 2010-04-05
forum: General Help
---

### Post by e24ohm on 2010-04-05
Folks:
I am running a Ubuntu install in Virtual Box; however, the max. res 800x600. My card and monitor will go higher, but the option is not available.

Where can I manual state that I want 1280x1024 and 32bit reolution? I looked in the /etc/X11/xorg.conf file; however, I was not sure what to change. I reviewed the same file on another machine, which is not in a Virtual issue, but the file only provied very generic entries, and did not have any detialed information that resembled 1280x1024 or 32 bit.

Thanks.

---

### Post by mickObrian on 2010-04-05
Hit your home key, default right control, (Ctrl on the right side) and press F, if the screen VirtualBox takes up your whole screen but there is a lot of black space around it, try pressing right control and G, this should auto-resize it, see if that works.
Edit: You might have to install guest additions for this to work, click "Devices" at the top and Install Guest Additions..." if what I said above doesn't work.

---

### Post by djoxyk on 2010-04-05
Guest Additions allow to set higher resolution. You need to install it from VM menu.

---

### Post by e24ohm on 2010-04-05
> **mickObrian said:**
> Hit your home key, default right control, (Ctrl on the right side) and press F, if the screen VirtualBox takes up your whole screen but there is a lot of black space around it, try pressing right control and G, this should auto-resize it, see if that works.
Edit: You might have to install guest additions for this to work, click "Devices" at the top and Install Guest Additions..." if what I said above doesn't work.Ok i will try Guest Additions....thanks

Hey...!!!! when will it be our time again for World Cup...1986 and still counting.

---

### Post by e24ohm on 2010-04-06
Even after installing the Extras, I still cannot get beyond 800x600. The option is not even available, so I am at a lost. I tried reviewing the /etc/X11/xorg.conf files; however, the entires look similar to other xorg.conf files I have on other Linux machines, which are not running in Virtual Box.

Need some suggestions on this issue.

---

### Post by mickObrian on 2010-04-06
Is your host OS Ubuntu as well?

---

### Post by Chris Musampa on 2010-04-06
> **e24ohm said:**
> Even after installing the Extras, I still cannot get beyond 800x600. The option is not even available, so I am at a lost. I tried reviewing the /etc/X11/xorg.conf files; however, the entires look similar to other xorg.conf files I have on other Linux machines, which are not running in Virtual Box.

Need some suggestions on this issue.

This might sound like a daft question, did you actually install the guest additions after clicking the menu item?

---

### Post by e24ohm on 2010-04-06
> **Chris Musampa said:**
> This might sound like a daft question, did you actually install the guest additions after clicking the menu item?Good question - after clicking the menu item, i ran the script, which was located on the dekstop, by a little CD-rom like icon. I am not 100% sure what it installed, since i did not reconize any of the details in the cli.

---

### Post by e24ohm on 2010-04-06
> **mickObrian said:**
> Is your host OS Ubuntu as well?NO, my host OS is windows Vista SP1

---

### Post by Chris Musampa on 2010-04-06
> **e24ohm said:**
> Good question - after clicking the menu item, i ran the script, which was located on the dekstop, by a little CD-rom like icon. I am not 100% sure what it installed, since i did not reconize any of the details in the cli.

As long as you run it with sudo it should install then you need to reboot the guest and you should be good to go.

---

### Post by e24ohm on 2010-04-06
I reinstalled my ubuntu guest OS, and was able to succesfully get 1024x768. Thanks; however, a nasty grey box is around the guest os screen, and the screen will not do full screen. What is the trick to remove the grey box?

thanks.

---

### Post by Chris Musampa on 2010-04-06
> **e24ohm said:**
> I reinstalled my ubuntu guest OS, and was able to succesfully get 1024x768. Thanks; however, a nasty grey box is around the guest os screen, and the screen will not do full screen. What is the trick to remove the grey box?

thanks.

I haven't had that, maybe check that 'seemless mode' and 'autoresize guest' are enabled.

---

### Post by karmic-koala on 2010-04-06
On your guest linux system issue the command

```
xrandr -s1280x800
```

replace the resolution with whatever x and y you want.

---

