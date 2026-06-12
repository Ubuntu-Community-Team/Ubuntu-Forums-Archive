---
title: "Crazy pair of questions...."
date: 2010-01-18
forum: General Help
---

### Post by JiuJitsu500 on 2010-01-18
Hello everyone.... I kind of ran into a crazy pair of things I noticed after having Karmic Ubuntu, installing Xfce and KDE and tweaking them to my liking, and how to separate their startup programs, etc..... even had to re-install ubuntu desktop from the package manager to get GDM to work right again.... but it's all beside the point.

Is there some kind of crazy limit to the amount of RAM read by the distro? I have 4GB in the computer, but running "free -m" and the system monitor both report 2.9GB.... not that it matters much, my swappiness is 0 and I run virtual box with Windows XP Vienna and Windows 7 and it still barely reaches 1.5GB..... but just wondering why it won't read the full 4GB.

And finally, I don't know what I did, but I do have Boot-Up Manager and got some things clicked and removed from start-up.... and it was working great, and still is. But, the GUI restart button (from the Gnome menu and the cairo-dock) causes the system to shut down completely, not restart. So, trying "sudo reboot" I get the same thing.... perhaps I caused some kind of screw-up in the reboot script? It shuts down fine, just will not turn back on by itself.... totally odd.

No further questions Your Honor! Thanks in advance, by the way. I've come here a million times and found the answers I was looking for without even signing up till a week or so ago...

Oh... and a random one.... "press ESC at the GRUB" does NOT bring up recovery.... it just beeps at me until I stop pressing it. I was going to run dpkg, but can't seem to get to it. I don't know a command to get into recovery from an already-booted GDM or full desktop in Gnome, Xfce, or KDE. Just curious.....

---

### Post by sxmaxchine on 2010-01-18
im not positive but i think the reason it wont display the full 4gb is because that some of the ram has been reserved for the system functions.

hope this helps you

---

### Post by s.fox on 2010-01-18
> **JiuJitsu500 said:**
> 

Oh... and a random one.... "press ESC at the GRUB" does NOT bring up recovery.... it just beeps at me until I stop pressing it. I was going to run dpkg, but can't seem to get to it. I don't know a command to get into recovery from an already-booted GDM or full desktop in Gnome, Xfce, or KDE. Just curious.....

Hello,

Karmic no longer has the ability to show the boot menu by pressing Escape. To get the boot menu to show, you have to hold down the *Shift* key during bootup. 

-Silver Fox

---

### Post by mcduck on 2010-01-18
Sounds like you are running a32-bit version of Ubuntu.

32-bit operating systems can only address a max of 4GB of memory. Since this address space also includes memory in your graphics card etc, the amount left for RAM will always be less than the full 4GB, depending on how much memory your other devices have.

If you had a graphics card with 2GB of memory there would only be 2GB worth of addresses for other use, so you'd see even less RAM than now.

You can either install the PAE-enabled 32-bit kernel, or install the 64-bit version of Ubuntu to use all your RAM. The later is of course only an option if you have a 64-bit processor.

(And no, the limitation is not in the distro, or even in Linux itself. It's a limitation of 32-bit computing in general and applies to all operating systems.)

---

### Post by 73ckn797 on 2010-01-18
> **mcduck said:**
> You can either install the PAE-enabled 32-bit kernel, ...........


This works for 32 bit.

---

### Post by JiuJitsu500 on 2010-01-18
McDuck... Fox....

Thanks for the reply to both of you, I kinda thought it had something about 32 or 64 but had no idea. It did happen when I had windows 7 too, thanks for the clarification on that. Also for the shift key thing... I'll try running throuh recovery now to see if I screwed anything up with the restart....

Would you say the 64-bit version is better? I know I didn't really notice much in other OS's, just shinier and preppier for a while.... but maybe Linux 64 can show me different....

Anyone have any ideas about the stupid restart thing? I again only really know it happened after installing KDE, Xfce, then the Ubuntu Desktop again to clear up the boot issues.... It simply will not restart through the GUI (cairo, menu) or through the terminal...

Thanks again!

---

### Post by Leppie on 2010-01-18
> **JiuJitsu500 said:**
> Oh... and a random one.... "press ESC at the GRUB" does NOT bring up recovery.... it just beeps at me until I stop pressing it. I was going to run dpkg, but can't seem to get to it. I don't know a command to get into recovery from an already-booted GDM or full desktop in Gnome, Xfce, or KDE. Just curious.....
at boot as Silver_fox_ said hold down shift.
in a xsession issue the following command:
```
sudo telinit 1
```
that's the number 1

---

### Post by mcduck on 2010-01-18
> **JiuJitsu500 said:**
> 
Would you say the 64-bit version is better? I know I didn't really notice much in other OS's, just shinier and preppier for a while.... but maybe Linux 64 can show me different....


Better? Well, it' not *worse* and it can fully use your hardware. There's no reason *not* to use a 64-bit Linux on a 64-bit computer. :)

Whether or not you'll see any performance increase depends on what kind of things you do with your computer. Not all tasks benefit from being able to handle larger numbers/higher precision. So, your desktop, and most of your applications, will run exactly the same on 64 bit system as they would run on a 32-bit system. Others, like many graphics, sound and video related tasks, can get a nice performance boost (if the programs you use are coded with 64-bit computers in mind)).

..and of course you'll e able to use all your RAM. :)

---

