---
title: "Can you help a rookie out? Trying to get use to Ubuntu (Ex-Windows user)"
date: 2011-10-30
forum: General Help
---

### Post by ebeeze on 2011-10-30
Hello,

I suppose I will introduce myself a bit before I state my problem. My  names Elvin, live in Miami, FL and have been using Windows all my life  pretty much. I am a student studying to get a bachelors in I.T and for that reason I decided to build my first computer and wanted to try and  use Ubuntu as my OS. Now Ubuntu is very different when it comes to  installing software and such. I am having a serious problem getting the  most minor things to work (I can't install Adobe Flash as I don't  understand how to install things onto my computer) I have read about  people using the terminal and inputting commands and such, but I really  don't know exactly how to do that, is there any way that I can just  download things with a wizard-like install? Any input is appreciated! I  downloaded Linux 11.10 64-Bit from the Ubuntu homepage and that is what I  am currently running. I would love to download Wine and install my games as that is why I actually made my computer (it's a gaming rig!). And I really love the foundations of why Ubuntu (Linux) was created; the entire idea of having a FREE OS and giving to the community really atttracts me to using Ubuntu. I really would love to learn how to be an avid Linux user.

P.S- Is there anywhere where I can learn how to use Ubuntu that you would recommend? & going back to the Adobe issue- I tried downloading Flash-Aid but it wouldn't let me, see picture link (photobucket) for more details

[http://s1185.photobucket.com/albums/z356/elvinblen92/?action=view&current=Screenshotat2011-10-30144052.png](http://s1185.photobucket.com/albums/z356/elvinblen92/?action=view&current=Screenshotat2011-10-30144052.png)

Thanks in advance!

---

### Post by techvish81 on 2011-10-30
use software centre or synaptic package manager, u will not have to use terminal..

---

### Post by ebeeze on 2011-10-30
> **techvish81 said:**
> use software centre or synaptic package manager, u will not have to use terminal..

That did the trick, well @ least for some things. I'm trying to update the Revision for my mobo from 1.0 to 1.1; I don't understand how to start the launcher for the installer and every time I click on a folder it says.

[IMG]http://i1185.photobucket.com/albums/z356/elvinblen92/Screenshotat2011-10-30152319.png[/IMG]

So what should I do from here?

---

### Post by lykwydchykyn on 2011-10-30
.exe files run in Windows (and sometimes DOS).  If you want to update the BIOS of your motherboard, I'd highly recommend doing it in an OS that the vendor has made the utility for.

Most motherboard BIOS utilities will run in DOS.  I've had good luck using freeDOS from a USB drive to update BIOS; you can find a tutorial here: [http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

---

### Post by ebeeze on 2011-10-30
I've actually already updatted my BIOS to the most current one, (i didn't have a choice, FX chips need it or they won't install any OS from what I've encountered) but need to now run the Revision disk my mobo (GA 990FXA-UD3) came with. The CD on the front shows Microsoft* Windows*7/Vista/XP. So how should i go about this?? Thanks again!

---

### Post by Carborundum on 2011-10-30
> **ebeeze said:**
> I've actually already updatted my BIOS to the most current one, (i didn't have a choice, FX chips need it or they won't install any OS from what I've encountered) but need to now run the Revision disk my mobo (GA 990FXA-UD3) came with. The CD on the front shows Microsoft* Windows*7/Vista/XP. So how should i go about this?? Thanks again!
'Revision' generally refers a version of the _hardware_. In other words, it cannot be updated, regardless of OS.

Motherboards usually ship with a disc containing drivers for various things. These are not needed in Linux, as all necessary drivers are included in the kernel itself.

---

### Post by ebeeze on 2011-10-30
> **Carborundum said:**
> 'Revision' generally refers a version of the _hardware_. In other words, it cannot be updated, regardless of OS.

Motherboards usually ship with a disc containing drivers for various things. These are not needed in Linux, as all necessary drivers are included in the kernel itself.
What do you mean exactly when you say "*all necessary drivers are included in the kernel itself."* i don't understand what you mean, what's the "Kernel"?

---

### Post by Gremlinzzz on 2011-10-30
> **ebeeze said:**
> What do you mean exactly when you say "*all necessary drivers are included in the kernel itself."* i don't understand what you mean, what's the "Kernel"?

[https://secure.wikimedia.org/wikipedia/en/wiki/Kernel_%28computing%29](https://secure.wikimedia.org/wikipedia/en/wiki/Kernel_%28computing%29)

---

### Post by lykwydchykyn on 2011-10-30
The kernel is the "heart" of the operating system, it's what talks to the hardware and gives the system a basic running environment.  In Linux it contains all the drivers for your hardware -- the software components that make your hardware work.  

There are a select few drivers that are not in the kernel, because of licensing issues, but you install those using the "hardware drivers" tool if you need them.

All those discs that came with your hardware can be put away somewhere safe for another day.  They are of no use on Linux, unless they specifically say they contain Linux drivers (and even then, they probably won't be up-to-date).

---

### Post by ebeeze on 2011-10-31
Thx! your replies have all been helpful and have given me a bit better of a knowledge-base for linux!=)

---

