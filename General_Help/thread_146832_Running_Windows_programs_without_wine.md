---
title: "Running Windows programs without wine?"
date: 2006-03-19
forum: General Help
---

### Post by Leiki on 2006-03-19
I REALLY want Ubuntu to be my one and only OS, but like most people not wanting to switch to Linux, I want to keep using my Windows programs.

Wine is to unstable and finiky for me to use...so I don't want to deal with it. I searched on google "windows programs on linux without wine" and found an article about WinToNet. It had a link to the website, and the whole website is gone. :(

Maybe I could use VMware. I've used it before but I don't know how I would point the virtual machine to my Windows partiton only... Is that possible? If not, does anyone want to share their insider tips in running windows programs on Ubuntu? ;)

---

### Post by joshuapurcell on 2006-03-19
Wine or Cedega are the only two ways I know of to actually run your Windows applications on your Linux install. Vmware will allow you to run Windows on Linux in a virtual computer. You would have to install Windows inside a VMware virtual server that runs on your Linux system. That could be done, and it may even be easier than getting Wine/Cedega to work (depending on what programs you want to use). Just remember that you would still need to install a completely different OS (i.e. Windows) on the VMware instance that you create.

---

### Post by CJs06 on 2006-03-19
Use cedega for windows games; Its a great emulator that runs my games good. It costs 5$ per month for a minimum of 3 months. After that you can stop paying but you wont get any updates.

There is crossover office which emulates most regular windows programs well such as photoshop, office, etc. It costs $40 for one copy.

---

### Post by lha on 2006-03-19
There's [qemu]("http://fabrice.bellard.free.fr/qemu/"), which is similar to VMWare. Qemu is in the repos, but if you want to make it faster with kqemu, the accelerator module, you have to compile it yourself. You can use a [script]("http://oui.com.br/n/content.php?article.23") to do the job.

---

### Post by JAwuku on 2006-03-19
I use [Parallels Workstation]("http://www.parallels.com") ([www.parallels.com](www.parallels.com)) to run Windows on top of my Ubuntu installation.

---

### Post by jdkchem on 2006-03-21
[QUOTE=JAwuku]I use [Parallels Workstation]("http://www.parallels.com") ([www.parallels.com](www.parallels.com)) to run Windows on top of my Ubuntu installation.[/QUOTE]

How do you like Parallels?  Can you use any usb devices such as a printer or external hard drive?

---

### Post by kosmic on 2006-03-21
You can also try CrossOver [http://www.codeweavers.com/]("http://www.codeweavers.com/") to run some Windows applicantions in Linux.

---

