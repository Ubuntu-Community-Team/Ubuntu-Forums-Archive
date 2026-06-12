---
title: "which virtual machine?"
date: 2010-06-07
forum: General Help
---

### Post by barna on 2010-06-07
Hi,
For my work I need to use Autodesk Inventor, which I am using now in the office of a colleague of mine - quite cumbersome to come over to him every time I need to work on the design of our project.
Very soon I will get a quite powerful notebook (Dell Inspiron 1564, with a Core i5 processor). That will be already a great comfort, not having to go over to his office - it would be even greater if I didn't have to reboot to windows every time.
Does it make sense to experiment with a virtual machine + Windows + Inventor installation? Can such a configuration run a serious 3D software reasonably? If yes, which virtual machine is recommended? Do programs installed under a virtual machine + windows have direct access to the graphics card, or is it only emulated like under wine? Any comments on this, what I should avoid, etc?
Thanks

---

### Post by ralanyo on 2010-06-07
I personally use vmware for all of my virtual machines. It runs nicely on Ubuntu with some pretty hefty applications. However, I have never tried something so graphics card intensive. Please let me know how this works out for you as I will be going through something similar in the coming months.

Thanks

---

### Post by ailmarpete on 2010-06-07
Yeah I do heaps of work with VM's, just for testing and self education.
VMWare seems to be the standard these days, I have just set up Workstation 7.1 on my new 64 bit Ubuntu installation today. No issues what so ever.
Workstation has supported 3D graphics in Windows VM's since version 7. Not that I have ever been running anything like you will be running, but I can say that Aero works fine on my Windows 7 64 bit VM.
I can also say that you will get considerable benefit in running a 64 bit host machine, that way you can run your VM with a decent amount of RAM, say 2 Gb's + and keep some for your host as well.
Cheers, Peter.

---

### Post by barna on 2010-06-24
I also went for VMware, installed Windows XP into it, and then installed Autodesk Inventor. However, without running too many applications, my memory (3 GB) was full, and the system started swapping (I installed a Windows version provided by our institute - this system has a central software management, and I do not really know what processes were running in the background...)
Still, I could start Autodesk Inventor, but already the GUI failed, the menu buttons (in the 'Ribbon') were completely screwed up. I gave it up at this stage (also being discouraged by a colleague of mine, who told me stories about a friend of her spending years on trying and failing to run 3D games under VMware+Windows)  and installed Windows 7 natively (the CD- or network-installation of XP [also provided by our institute] crashed). 
So no good news on the VM side.

However, the machine (Dell Inspiron 1564) works perfectly with kubuntu 10.04, every single hardware worked out of the box (webcam, suspend to RAM, video card, wireless after installing the proprietary driver)

---

