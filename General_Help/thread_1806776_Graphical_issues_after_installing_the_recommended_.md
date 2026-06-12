---
title: "Graphical issues after installing the recommended propietary nvidia driver."
date: 2011-07-18
forum: General Help
---

### Post by Veren on 2011-07-18
Hello there,
I am using a 64-bit version of Natty at the moment. I have nvidia gtx460m graphics in my laptop. After doing a fresh install and update&upgrade, I went on and installed the recommended driver from "additional drivers" submenu in preferences.

I didn't uninstall nouveae drivers, I don't know whether it does that by itself, but I didn't want to do anything stupid.

Now I have the recommended driver installed, it:
1. says: Driver is activated, but not in use.
2. when running Ubuntu Classic or Unity, the performance of metacity and window management is rather sluggish, just as are the other effects. I don't believe there should be an issue with that with this gpu.
3. when turning off the laptop, it says: "disconnected from plymouth" in yellow, along with a bunch of other processes in yellow as well. I can't make a screenshot and I don't know how to post it, sorry. I would prefer it only to show the "Ubuntu" logo, if possible - it did so in 10.04, when I started.
4. when turning on the laptop, some message about "mountall" pops up. In yellow.
5. When I am turning off the computer, the resolution of that "Ubuntu" sign and of the five dots is very low - it fills about quarter of my screen, and it definitely insn't in the 1920x1080 resolution I otherwise use.

Thank you, have a nice day (:

---

### Post by HiImTye on 2011-07-18
> **Veren said:**
> Hello there,
I am using a 64-bit version of Natty at the moment. I have nvidia gtx460m graphics in my laptop. After doing a fresh install and update&upgrade, I went on and installed the recommended driver from "additional drivers" submenu in preferences.

I didn't uninstall nouveae drivers, I don't know whether it does that by itself, but I didn't want to do anything stupid.

Now I have the recommended driver installed, it:
1. says: Driver is activated, but not in use.
2. when running Ubuntu Classic or Unity, the performance of metacity and window management is rather sluggish, just as are the other effects. I don't believe there should be an issue with that with this gpu.
3. when turning off the laptop, it says: "disconnected from plymouth" in yellow, along with a bunch of other processes in yellow as well. I can't make a screenshot and I don't know how to post it, sorry. I would prefer it only to show the "Ubuntu" logo, if possible - it did so in 10.04, when I started.
4. when turning on the laptop, some message about "mountall" pops up. In yellow.
5. When I am turning off the computer, the resolution of that "Ubuntu" sign and of the five dots is very low - it fills about quarter of my screen, and it definitely insn't in the 1920x1080 resolution I otherwise use.

Thank you, have a nice day (:
2) that's to be expected without 2D or 3D acceleration
5) that's because the final screen isn't using a front end that supports complex graphics

the rest would require more information to answer
did you do a fresh install?
did you check to make sure your graphics card is supported by the 'recommended driver'?
what is the exact message you receive about 'mountall'?

---

### Post by Veren on 2011-07-18
> **HiImTye said:**
> 

the rest would require more information to answer
did you do a fresh install?
did you check to make sure your graphics card is supported by the 'recommended driver'?
what is the exact message you receive about 'mountall'?

I did a fresh install yesterday, there is no other OS on the laptop at this moment and the only things I did were doing updates, installing the theme and nautilus elementary. But the issues I wrote have been here since I installed the driver, what was what I did right after I had installed the updates.

Are there reasons to believe that the graphic card is not supported ? No I didn't check anything to be honest, I believed it was universal, or that it had recognized the correct driver by itself.

---

### Post by HiImTye on 2011-07-18
> **Veren said:**
> I did a fresh install yesterday, there is no other OS on the laptop at this moment and the only things I did were doing updates, installing the theme and nautilus elementary. But the issues I wrote have been here since I installed the driver, what was what I did right after I had installed the updates.

Are there reasons to believe that the graphic card is not supported ? No I didn't check anything to be honest, I believed it was universal, or that it had recognized the correct driver by itself.
you can always try the driver from the [nVidia site]("http://www.nvidia.com/Download/index.aspx?lang=en-us") but there's no guarantee that it will integrate properly with Ubuntu (odds are it will work but you never know)
it will come in the form of a .run and you will need to run it without being in a graphical session

---

### Post by Veren on 2011-07-18
Yes, I will give it a try. I believe I should remove this one first, right ?
Just to make sure, the "while not a graphical session" means:
1. alt+ctrl+f1
2. login
3. type /home/name/Downloads/nameofdriver ? I am not very good with this, sorry, the only thing I installed trough something other than aptitude is libreoffice.

---

### Post by HiImTye on 2011-07-18
no, you'll need to not have GDM running at all so you'll need to reboot into a terminal console

edit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to 
GRUB_CMDLINE_LINUX_DEFAULT="single"

and then sudo update-grub

reverse to boot back into graphical interface

to run the driver you will need to know its' location (including caps as folders in *nix are case-sensitive). you can often times skip all the typing by typing a few letters and hitting tab (saves a lot of time if you are running some long convoluted file name) you will run it like this:

sudo sh /path/to/file/filename.run

---

### Post by Veren on 2011-07-18
I have just learned some new things and I am grateful to you for that, however, there seems to be an issue with nouveau drivers being active. It asked to create a modprobe, where I agreed, but it didn't help, so I rebooted and deleted the modprobe, then rebooted again into graphical interface.

I believe the issue comes down to this: I think I need to delete the nouveau drivers. If something goes horrible wrong, can I restore them ? 

Oh, and to answer the mountall, it says :
"mountall: disconnected from plymouth"
but it doesn't do that since I have removed the recommended nvidia driver. Also, I only have the Ubuntu sign on when turning off the computer and it's in my native resolution (1920x1080). But I would really like the 3D acceleration too !

Thank you (:

---

