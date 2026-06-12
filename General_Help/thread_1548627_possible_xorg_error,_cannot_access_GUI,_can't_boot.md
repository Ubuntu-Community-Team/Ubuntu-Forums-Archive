---
title: "possible xorg error, cannot access GUI, can't boot from CD"
date: 2010-08-08
forum: General Help
---

### Post by Jimboted on 2010-08-08
Hi All,

I started using ubuntu a few weeks ago and have been loving it. 

Unfortunately today, whilst attempting to run dual monitors, I appear to have done something cataclysmic... details as follows:

AMD Athalon 64 3700 processor
GeForce 6700 

Was attempting to get second monitor to work, in the process of this modified xorg.  When I rebooted the computer froze on the Ubuntu splash screen.

After several hours on various forums the machine started booting in the terminal, but startx would not take me into the GUI.

When running Startx I get the following errors:

[drm] failed to open device
VESA (0): No valid mode
Screen(s) found, but none have a usable configuration


Along the way, I seem to have managed to remove xorg and cannot figure out how to reinstall it.

Have attempted to recover the installation from the Ubuntu installation CD, but for some reason the PC is no longer able to boot from the CD in spite of this being setup correctly in the BIOS.


Consequentially I am very much at my wits end.  Any advice people can offer would be much appreciated.  Happy to provide any additional information required to assist.

Cheers,


Jim

---

### Post by linux18 on 2010-08-08
```
 sudo dpkg-reconfigure xserver-xorg && xinit & sleep 3 &&  killall xinit && sudo reboot 
```

---

### Post by Jimboted on 2010-08-08
Hi Linux18, thanks for the speedy response!

Attempted the above code, this have me message saying xinit: no such file or directory etc.

Therefore tried sudo apt-get install xinit

this appears to have run correctly, 

Then re-entered your code, computer restarted and returned to the same three error messages.

Can you offer any other suggestions?  (or can i provide details of any reports to help).


Many thanks,


Jim

---

### Post by linux18 on 2010-08-08
```
 sudo mv /etc/X11/xorg.conf /etc/X11/xorg.bak && sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf 
```

---

### Post by WorMzy on 2010-08-08
Which version of Ubuntu are you using?

If 10.04 (or higher) try deleting /etc/X11/xorg.conf, then running startx again.

Else try deleting that file then running nvidia-xconfig.

---

### Post by Jimboted on 2010-08-09
Hi,

Using version 10.04.

Got it to work by deleting /etc/X11/xorg.conf, then then running nvidia-xconfig. 

This has got me back into Ubuntu GUI.  didn't have time to see whether this has affected the booting from CD issue, but will check again tonight & post results here.

Thanks again for everyone's suggestions in the meantime.


another quick question - can anyone suggest a good resource for me to use to learn about terminal use in greater depth?

Thanks,


Jim

---

### Post by Jimboted on 2010-08-09
OK, so got home from work and had a look.  I'm back into Ubuntu. 

But now, maddeningly, I can't seem to raise my screen resolution above 640x480 - whilst there is some weird retro pleasure in this it is totally unpractical.


Have tried checking system > preferences > hardware drivers that hasn't helped.

Before somebody asks I have also been to system > preferences > monitors, but I can only select 640 x 480 or less.


Does anyone have any suggestions?

Thanks,


Jim

---

### Post by Jimboted on 2010-08-10
in case anyone looking for solution to the old 640x480 problem eventually overcame this by 

ctrl-alt-F1

sudo /etc/init.d/gdm stop

that and a quick reboot seems to have done the job.

Thanks to all those who provided advice.


Jim

---

