---
title: "How to run Windows as virtual machine on Ubuntu 9.04 or 9.10"
date: 2009-12-11
forum: General Help
---

### Post by vwhit09 on 2009-12-11
I currently have Ubuntu 9.04 and urgently need to use a Window's supported software on my laptop. I was told I can run Windows as a virtual machine application as a guest on Ubuntu 9.04 or 9.10. Any specific instructions on how to do this? Thanks.

---

### Post by bluelamp999 on 2009-12-11
Use VirtualBox - [http://www.virtualbox.org/](http://www.virtualbox.org/)

If you've a Windows installation disk you can install a virtual Windows machine on your 'buntu system.

It's all pretty easy and there's lots of tutorials on the web.

Good luck...

Oh, and there's also the Wine application ([http://www.winehq.org/](http://www.winehq.org/)) which can run a lot of Windows apps under Linux

---

### Post by joes7 on 2009-12-11
Virtual Box is probably the best, but if you want to try something else use VMware

---

### Post by blur xc on 2009-12-11
> **vwhit09 said:**
> I currently have Ubuntu 9.04 and urgently need to use a Window's supported software on my laptop. I was told I can run Windows as a virtual machine application as a guest on Ubuntu 9.04 or 9.10. Any specific instructions on how to do this? Thanks.

[http://www.tomshardware.com/reviews/xp-mode-ubuntu,2434.html?xtmc=linux&xtcr=3](http://www.tomshardware.com/reviews/xp-mode-ubuntu,2434.html?xtmc=linux&xtcr=3)

I did it w/o any guide, it's not that hard, but make sure you read the manual.  The VBox forum is a good place to go for help, but they are not that tolerant of questions asked that are covered in the manual and/or in sticky's.  

BM

---

### Post by pricetech on 2009-12-11
I'm running Hardy, but:
I installed the version of VirrualBox from the repos.  XP works like a charm for me.  Just make sure you Install Guest Additions.  And don't try to install drivers either.  Use the vbox drivers.  You may have to tinker with choices under sound and network to make things work, but that's the most I've had to do.

---

### Post by waynep on 2009-12-11
Another option is Vmware player. The new version allows you to create VM's in addition to playing them. I am running VMware Player 3 on my Win 7 machine. Ubuntu 9.10 is a VM so I am opposite you but it's works great. I have never tried VirtualBox.

---

### Post by vwhit09 on 2009-12-15
> **waynep said:**
> Another option is Vmware player. The new version allows you to create VM's in addition to playing them. I am running VMware Player 3 on my Win 7 machine. Ubuntu 9.10 is a VM so I am opposite you but it's works great. I have never tried VirtualBox.
Is VMware free? I just googled Vmware and I saw VMware workstation 7 at $189. Can you direct me to the free options.

---

### Post by dcstar on 2009-12-16
> **vwhit09 said:**
> Is VMware free? I just googled Vmware and I saw VMware workstation 7 at $189. Can you direct me to the free options.

VMware Server is free.

All the VM info is already in the Virtualization forum, where this thread should also be.

---

### Post by vwhit09 on 2009-12-22
Thanks David. Guys, I've been having problems with installing the guest Microsoft VM. In the middle of the process there is a warning that says "FATAL: No bootale medium found! System halted". I have the installation disk of Microsoft 2003 which I designated as the guest OP to add but when I put into my CD ROM drive nothing happens. Can somebody help!

---

### Post by vwhit09 on 2009-12-22
> **pricetech said:**
> I'm running Hardy, but:
I installed the version of VirrualBox from the repos.  XP works like a charm for me.  Just make sure you Install Guest Additions.  And don't try to install drivers either.  Use the vbox drivers.  You may have to tinker with choices under sound and network to make things work, but that's the most I've had to do.
Thanks for message. I started dowloading the software from the Synaptic Package Manager and have been having some problems advancing. You warned not to try installing drivers, but instead the vb's drivers. How do I do this. I came across a warning that says I have assigned more than 50% of my computer's memory to the virtual machine that there might be a risk. I used an external hard drive to start the installation. Was this the wrong move?

---

### Post by Vaphell on 2009-12-22
you can change how much memory vm gets, it all depends on what you want to do with it. Warning is there to inform you that you can cripple performance of your host os if you leave to little for it to function.

about drivers - don't install windows drivers for your hardware because they won't be talking to the hardware directly. You need vbox drivers to communicate with host os about what needs to be done with computer devices. It should be streamlined by virtualbox itself though, so don't worry.

---

### Post by spydeyrch on 2009-12-22
Setting up a VM with VB should be pretty straight forward. if you need some help, try one of my posts [here.]("http://ubuntuforums.org/showthread.php?p=8505244#post8505244") You can always follow the manual/guide that VB has made on their website. Also, post any issue in the thread. good luck!! :KS
 
the same setting should apply except you will need to select windows -> xp in stead of ubuntu. 
 
Also, make sure that you make any necesary changes due to you hardware being possilby different than the guys in the other thread that I linked to. Have fun and enjoy your VM. 
 
 
-Spydey :guitar:

---

### Post by vwhit09 on 2009-12-22
Thanks. So, you are saying that I do not need the installation package from Windows 2003 that I have. I'm sorry, I'm not as literate as you with my basic questions, but I don't know what the vbox drivers are? How do I locate and access them during the installation process once I open the virtual box program on my computer?

---

### Post by pricetech on 2009-12-22
> **vwhit09 said:**
> Thanks for message. I started dowloading the software from the Synaptic Package Manager and have been having some problems advancing. You warned not to try installing drivers, but instead the vb's drivers. How do I do this.

To clarify;  you won't be installing any drivers at all.  VirtualBox includes "hardware" which winders should be happy with.


> **vwhit09 said:**
>  I came across a warning that says I have assigned more than 50% of my computer's memory to the virtual machine that there might be a risk.

Assigning too much of your RAM to the VM could cripple your host.


> **vwhit09 said:**
>  I used an external hard drive to start the installation. Was this the wrong move?

Shouldn't matter, as long as the setup files are there.

One more thing;  You may be prompted to activate winders.  If the computer came with winders you should be able to use the License number from the COA sticker on the machine.

---

### Post by vwhit09 on 2009-12-22
Also, do I need to use an external hard drive as the hard drive needed for installation?

---

### Post by spydeyrch on 2009-12-22
> **vwhit09 said:**
> Also, do I need to use an external hard drive as the hard drive needed for installation?
 
 
You shouldn't have to. VB will place your VM in the .Virtual Box folder in your /home. You will need the windows 2003 install disk that you have to install windows into your VM. virtual box will install the needed drivers for windows automatically. :)
 
-spydey   :guitar:

---

### Post by vwhit09 on 2009-12-23
Thanks. I figured the "hard drive", but now when I press to start the process on the black terminal screen it says "Fatal: No bootable medium found! System halted". Why is this showing up when I have the Windows 2003 installation disk in my CD drive? I do have to insert this CD right, in order for the vb lead me to the next step of adding Windows 2003 as a host. I'm stuck at this point. Someone please help.

---

### Post by ajaay on 2009-12-23
> **vwhit09 said:**
> Thanks. I figured the "hard drive", but now when I press to start the process on the black terminal screen it says "Fatal: No bootable medium found! System halted". Why is this showing up when I have the Windows 2003 installation disk in my CD drive? I do have to insert this CD right, in order for the vb lead me to the next step of adding Windows 2003 as a host. I'm stuck at this point. Someone please help.
 What i say might not be the same everybody else do.. but worked good for me..
As u get that "fatal" message, click on Devices select cd drive(yours).
After it is selected go to the first menu(forgot the name since not working with it right now:)) and click reset.  
Make sure in the settings for Virtual machine that u put cd/dvd as the main bootable for installation.
As u reset the machine, it will boot from ur cd and there u go.:popcorn:

---

### Post by spydeyrch on 2009-12-23
> **vwhit09 said:**
> Thanks. I figured the "hard drive", but now when I press to start the process on the black terminal screen it says "Fatal: No bootable medium found! System halted". Why is this showing up when I have the Windows 2003 installation disk in my CD drive? I do have to insert this CD right, in order for the vb lead me to the next step of adding Windows 2003 as a host. I'm stuck at this point. Someone please help.
 
 
Before you start the vm, select it by doing a single click, then go to settings, go to CD/DVD on the left menu and then on the righthand side, make sure that you have CD/DVD selected, then select the optical drive that you are inserting you media into. also check the pass through box. 
Once you are done with that, go back to the main VM menu and start the VM. it should look for the media that you placed optical drive PRIOR to starting the VM. It should find it. Give that a whirl.
 
If that doesn't work, let me know and we will walk through setting up a VM from scratch for your windows 2003. I find that doing it from scratch is the best way to do it. It might be a little time consuming but I am pretty sure that it will work. I have several VM through VB and they are all work fine. I have a some with Win7 as host and ubuntu 9.10 x64 as host and some as ubuntu 9.04 x64 & x32 as host. We will get this working one way or another.
 
Before we do that though, if what I just told you doesn't work, make sure you give us your machine specs: Processor (CPU), Motherboard (Mobo), RAM, Graphics Card (GPU), Hard Disks (HDD), Host operating system (OS) and version. then we will get things rolling. :)
 
Try what I mentioned first though as that should help. Let us know.
 
-Spydey:guitar:

---

### Post by vwhit09 on 2009-12-23
Thanks Sydey for the patience and help. I did try that option you gave me and checked the pass through box but no success yet. I did so something different this time that I had not done before where I pressed f12 as prompted when the black screen first came on. After pressing f12 another screen comes up that says the following: 

Detected Hard Disks: 

IDE controller: 

1) Primary Master

Other boot devices: 

f) Floppy
c) CD-ROM
l) LAN

b) Continue booting

From this I did not know what to do but the most logical was to try c) and b). I did this but in both cases the same initial error came up as NO BOOTABLE MEDIUM found!

Now I will post the specs you needed.

---

### Post by vwhit09 on 2009-12-23
Spydey, 

My specs are CPU= Celeron M 1.46 GHz
Don't know mobo
RAM = 512 MB SODIMM
Graphics card = ?
Hard Disks = 40GB
Host OS = Linux (Ubunt 9.04)

---

### Post by spydeyrch on 2009-12-23
> **vwhit09 said:**
> Spydey, 
 
My specs are CPU= Celeron M 1.46 GHz
Don't know mobo
RAM = 512 MB SODIMM
Graphics card = ?
Hard Disks = 40GB
Host OS = Linux (Ubunt 9.04)
 
I am at work right now, but when I get home, I will try and post the steps that should help you get everything working. Cross your fingers. To be honest, I doubt that it will work because you have such a low amount of ram. Let em rephrase that, we should be able to get it up and running BUT, your cpu and the amount of ram are going to significantly make things difficult.
 
Once I get home, I will post. I will need to do some research first on windows 2003's system requirements as I haven't used that os for a long time. Until then!
 
-Spydey :guitar:

---

### Post by dcstar on 2009-12-23
> **spydeyrch said:**
> 
.........
Once I get home, I will post. I will need to do some research first on windows 2003's system requirements as I haven't used that os for a long time. Until then!


Windows 2003 is a server platform that would run like a POS natively on that hardware spec, and isn't worth bothering about as a VM as that hardware spec isn't good enough to run any sort of viable VM.

---

### Post by vwhit09 on 2009-12-23
> **dcstar said:**
> Windows 2003 is a server platform that would run like a POS natively on that hardware spec, and isn't worth bothering about as a VM as that hardware spec isn't good enough to run any sort of viable VM.
Thanks David. So what does run like a "POS natively" mean? So pretty much until I upgrade my specs then I won't be able to run the VM? Today I just ordered another 512MB RAM that would give me a total of 1GB for my computer. What other specs would I need to upgrade in order for the VM to work?

---

### Post by Vaphell on 2009-12-23
POS = piece of sh!t
he's saying that W2003 would be horrible natively running on that old hardware so with additional overhead (host os, virtual machine taking up resources) you'd enter the world of pain (assuming it would work at all)

---

### Post by spydeyrch on 2009-12-23
That is what I was saying, that due to your cpu and ram, it will probably not work but I am willing to help you give it a try if you would like to. I can't guarantee anything because of your specs but I can at least try to help.

You have another option, what windows native software are you trying to run? There is most likely a linux/ubuntu native version of the same type of software, and the best thing is that it is FREE!!! :popcorn:

What would you like to do? Make the VM and give it a try, or find a linux alternative?

Let us know.  :)

-Spydey  :guitar:

---

### Post by dcstar on 2009-12-23
> **Vaphell said:**
> POS = piece of sh!t
he's saying that W2003 would be horrible natively running on that old hardware so with additional overhead (host os, virtual machine taking up resources) you'd enter the world of pain (assuming it would work at all)

Exactly. An extra 512 of RAM will make a major difference, but unless you only leave a 300MB for the host that is still only 700 for the VM.

It will probably improve from totally hopeless to virtually (no pun intended) unusable.

---

### Post by spydeyrch on 2009-12-29
@vwhit09 - any updates? do you still need some help?
 
-Spydey  :guitar:

---

