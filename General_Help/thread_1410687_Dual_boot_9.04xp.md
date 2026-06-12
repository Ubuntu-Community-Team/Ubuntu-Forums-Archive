---
title: "Dual boot 9.04/xp"
date: 2010-02-19
forum: General Help
---

### Post by accodata on 2010-02-19
Hi
I am a converted ubuntu user, however I need to install some xp programs, that I can't get to work with 9.04 even with wine.

So how do I put windows on a pc that has Linux on???????

I can be pretty dim, so help needs to be basic, step-by-step if you are able to help!!

with thanks

Accodata

---

### Post by hiakaash on 2010-02-19
I've also recently switched to ubuntu from XP. After switching to ubuntu i also wanted to run some XP programs so, I installed Virtualbox (It's available for free as most of the other softwares). Now, I'm using XP as a virtual machine and ubuntu as the main OS & I'm quite impressed with the performance too...I've alloted 1 gb ram and 20gb disk space for XP...  my system is 2.7 Core2Duo with 4gb Ram and 500 gb HDD(if you asked)... Cheers!

---

### Post by akakingess on 2010-02-19
hiakaash is right, doing it via virtual ware, whatever you choose is probably the simpler way out at this point, otherwise you are going to have to back everything up and install XP first (my recommendation, not the requirement) and then install Ubuntu back on there. Not really a problem and we could help you through it, but how much will you be running XP anyways?  If the answer is not much, you may just want to run it virtually, which just means you would boot into Ubuntu, and then "run" (for lack of a better word) XP within Linux, but it would be like it's own OS. I hope that makes sense, and let us know which way you decide to go and we (the wonderful Ubuntu community) will be glad to help you out.

---

### Post by accodata on 2010-02-19
ok, told you I can be dim
what is the difference about dual booting and Virtualbox?

---

### Post by accodata on 2010-02-19
I will only running 3 programs in Xp.

---

### Post by JosephMarc on 2010-02-19
There's a tutorial here : 
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by akakingess on 2010-02-19
The difference is the way the OS is run, if you are dual-booting then you will actually have a "seperate" installation of XP installed and need to choose it from the Grub menu while booting up the computer. However, if you install it "virtually" (via VMware or Virtual Box) then you will always boot the computer into Ubuntu and if you need to get into or run a Windows app, you will run the virtualization software which will launch Windows within Ubuntu, you can use Windows and then exit out and still have Ubuntu running.

---

### Post by hiakaash on 2010-02-19
> **accodata said:**
> ok, told you I can be dim
what is the difference about dual booting and Virtualbox?
In dual booting you've to select an OS to boot (in this case either Ubuntu or XP) and It will boot up indipendently whereas, a virtual machine is a software (e.g. VirtualPC, VMvare, VirtualBox etc) that executes programs like a physical machine on the main OS... just google it to understand it more...:popcorn:

---

### Post by Jackzor on 2010-02-19
sudo apt-get install virtualbox-ose

Open it. You will get it figured out I'm sure.

Try this first. If you don't like it then you may remove it and go with the dual boot. But.. you will most likely use this.

---

### Post by accodata on 2010-02-19
Firstly, THANK YOU 

Next, do I actually install XP on this virtualbox?

---

### Post by Jackzor on 2010-02-19
> **accodata said:**
> Firstly, THANK YOU 

Next, do I actually install XP on this virtualbox?

Yes. You will have to mount the XP iso file in virtualbox and it will load the cd and start the installion.

The VM is JUST like a normal computer.

---

