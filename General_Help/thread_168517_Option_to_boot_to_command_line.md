---
title: "Option to boot to command line"
date: 2006-04-30
forum: General Help
---

### Post by sadjack on 2006-04-30
Hi

I would like an option within grub to boot to a command line instead of X. Ideally  the default would be to X but on occasion when I wanted, boot to CLI.

How can I do that?

Cheers

---

### Post by Qrk on 2006-04-30
You can get rid of gdm by uninstalling it, or you can just stop it from running. I'd recommend the latter. 

```
sudo chmod -x /etc/init.d/gdm
```

I think this is the best way to do it.

(You can still get Gnome by 'startx')

---

### Post by Ramses de Norre on 2006-04-30
Setting gdm unexecutable will prevent you from running it at all..
I'd install sysv-rc-conf and disable gdm for runlevel 2 if you want to boot without it all the time. You can start it with sudo /etc/init.d/gdm start then or use startx to load the default gui.
I don't know about any grub options for it..

---

### Post by 3dmonkey3000 on 2006-06-28
Is there an option like the one that Redhat 8 has, where you just edit the inittab file and change ":initdefault:5:runlevel" to ":initdefault:2:runlevel" etc??
Or one such as this one:
> **From [http://redhat.activeventure.com/8/referenceguide/s1-grub-runlevels.html](http://redhat.activeventure.com/8/referenceguide/s1-grub-runlevels.html)**
-------------------------------------------------------------------------
Changing Runlevels at Boot Time

Under Red Hat Linux, it is possible to change your default runlevel at boot time.

If you use LILO as your boot loader, access the boot: prompt by typing [Ctrl]-[X]. Then type:

linux number

In this command, replace number with either the number of the runlevel you wish to boot into (1 through 5), or the word single.

If you are using GRUB as your boot loader, follow these steps:

    *

      In the graphical GRUB boot loader screen, select the Red Hat Linux boot label and press [e] to edit it.
    *

      Arrow down to the kernel line and press [e] to edit it.
    *

      At the prompt, type the number of the runlevel you wish to boot into (1 through 5), or the word single and press [Enter].
    *

      You will be returned to the GRUB screen with the kernel information. Press the [b] key to boot the system. 
??

---

### Post by Yfrwlf on 2007-02-17
> **3dmonkey3000 said:**
> Is there an option like the one that Redhat 8 has, where you just edit the inittab file and change ":initdefault:5:runlevel" to ":initdefault:2:runlevel" etc??
??

The program mentioned, sysv-rc-conf is a method to edit runlevels, I just tried it and it works great.  I was looking for a nice way of editing runlevels from the command line and that's it.  There are other ways too of course but that one is easier since you don't have to learn more commands.  Another option is to boot your machine into a lower runlevel by specifying a number at the end of the boot string in GRUB.  Now, as for where the runlevel entries are stored that sysv-rc-conf modifies, I'm not sure.

---

