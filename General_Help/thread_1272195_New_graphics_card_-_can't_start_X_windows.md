---
title: "New graphics card - can't start X windows"
date: 2009-09-21
forum: General Help
---

### Post by raguru on 2009-09-21
I am running Kubuntu 9.04 on my desktop.  Recently my geforce 6200 graphics card died.  I replaced it with a geforce 8400 graphics card.  Now, when I try to boot, I see the Kubuntu logo and blue bar that moves as it loads.  But at the end of it, instead of giving me a login screen, it switches to large text mode and I get:

Not starting g Display Manager; it is not the default display manager.

which is ok since I do have kdm as the default manager.

Then it goes through some checks and stops without any particular error.  

By pressing Ctrl-Alt-F1, I am able to get to the text login and I am able to login.  But pressing Ctrl-Alt-F7, I don't get the graphics login screen.  

What should I do to fix this?  Is it not finding drivers for my new graphics card?  The same thing happened when I tried to boot before I installed the new graphics card.  I was hoping it would boot with the integrated graphics on the motherboard, but it did not.  

I would appreciate any help.  Thanks in advance.

-Raghu

---

### Post by kimo9909 on 2009-09-24
> **raguru said:**
> I am running Kubuntu 9.04 on my desktop.  Recently my geforce 6200 graphics card died.  I replaced it with a geforce 8400 graphics card.  Now, when I try to boot, I see the Kubuntu logo and blue bar that moves as it loads.  But at the end of it, instead of giving me a login screen, it switches to large text mode and I get:

Not starting g Display Manager; it is not the default display manager.

which is ok since I do have kdm as the default manager.

Then it goes through some checks and stops without any particular error.  

By pressing Ctrl-Alt-F1, I am able to get to the text login and I am able to login.  But pressing Ctrl-Alt-F7, I don't get the graphics login screen.  

What should I do to fix this?  Is it not finding drivers for my new graphics card?  The same thing happened when I tried to boot before I installed the new graphics card.  I was hoping it would boot with the integrated graphics on the motherboard, but it did not.  

I would appreciate any help.  Thanks in advance.

-Raghu

Try this...I'm not sure if it will work but it might.

1) Press Alt + F2 and then type 'gksu nvidia-settings' to bring up the NVidia X Server Settings dialog.
2) Choose 'X' Server Display Configuration
3) Then make the necessary changes and save the configuration.

---

### Post by gillespiea on 2009-09-24
Hi, i use 2x Nvidia GeForce 8800GS and sadly they dont work with the linux kernal used in ubuntu 8.10 and 9.04...i assume its a driver issue. I've looked all over for an answer to see if it's something else but sadly all is pointing to the driver incompatible with the kernal.

---

### Post by gillespiea on 2009-09-24
just thought i'd add. I use 8.04 LTS and it works fine.

---

