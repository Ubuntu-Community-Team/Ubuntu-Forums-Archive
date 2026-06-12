---
title: "safe mode / screen settings recuperation"
date: 2009-10-15
forum: General Help
---

### Post by yanvolking on 2009-10-15
Hello Community,

When I change the screen settings, If I get it wrong, the whole screen image can become scrambled.  I believe for example that this can happen when the refresh rate is set wrong.  The problem is that once this has happened, it is a hit and miss affair to get back to the right menu and rectify the settings (ie you have to navigate the mouse on a scrambled image - NOT EASY and very stressful).

In windows, when this happens you can boot up in safe mode and the screen image is simpler but clear, thus enabling you easily to return to the screen settings window and rectify whatever you want.

I have not been able to find such a function in UBUNTU.  

Does one exist?  if so how does one access it?
If not, what is the best course of action if the screen becomes scrambled?

Thanks

---

### Post by P4man on 2009-10-15
you can boot recovery mode, select a root shell and then run
```
dpkg-reconfigure xserver-xorg
```

the recovery mode also has an option called "xfix" I believe, though I never tried it, i guess its there to fix problemsn with X :)

lastly, you can edit your xorg. conf by hand if you want and know what you're doing:

```
nano /etc/X11/xorg.conf
```

---

### Post by yanvolking on 2009-10-15
Hi P4man,

Thanks for your reply.  I am a complete novice in Ubuntu and computing in general.  I am familiar with GUI environments but so much with command line management.  If I fololow your instruction to boot in recovery mode and enter 
dpkg-reconfigure xserver-xorgWill that bring me to something resembling a screen settings menu so that I can go back to the original settings, or will there merely be an invitation to enter lots of line commands?
Can I play around with the 
dpkg-reconfigure xserver-xorg

command without risking irreversable damage/changes to my general settings?

Thanks

Yan

---

### Post by P4man on 2009-10-15
> **yanvolking said:**
> Hi P4man,

Thanks for your reply.  I am a complete novice in Ubuntu and computing in general.  I am familiar with GUI environments but so much with command line management.  If I fololow your instruction to boot in recovery mode and enter 
dpkg-reconfigure xserver-xorgWill that bring me to something resembling a screen settings menu so that I can go back to the original settings, or will there merely be an invitation to enter lots of line commands?
Can I play around with the 
dpkg-reconfigure xserver-xorg

command without risking irreversable damage/changes to my general settings?

Thanks

Yan

It will run a (non graphical) wizard to guide you through resetting your xorg configuration (X.org or X is the windowing manager of linux. Basically what you need to have a GUI at all).

Playing around with it will not do "irreversable" damage, but it can mess up your configuation file if you feed it wrong information, rendering your ubuntu setup without working GUI and it will disable any accelerated drivers I think, unless you run it with a "-p high" switch. Then again, Im not entirely sure.

If you have an nvidia card, and installed the nvidia drivers, you can also use a different command:

nvidia-xconfig

IIRC, it will "automagically" set your X config, but if it was nvidia drivers that caused your screen to get garbled in the first place, it might not be the best idea :)

---

