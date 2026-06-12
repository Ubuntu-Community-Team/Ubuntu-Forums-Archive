---
title: "Virtual box set up failed! Help!"
date: 2009-10-09
forum: General Help
---

### Post by Camilia on 2009-10-09
I followed the instruction to set up the virtual box.  Then inserted the CD. The result is not bootable media found. System halted. 

What can I do?

---

### Post by mechro on 2009-10-09
What is the CD?

---

### Post by Camilia on 2009-10-09
It is Watchtower library CD, CD WTLIBO7E

---

### Post by mechro on 2009-10-09
OK. Sorry, I was alluding to the OS.

How about?... What version of Windows have you installed in the Virtual Box?

---

### Post by Camilia on 2009-10-09
Windows xp. Been told that the CD is a Windows program and rated platinum for wine.

---

### Post by mechro on 2009-10-09
How would you run the Watchtower CD from Windows? Do you boot the CD or insert it when you are running XP?

---

### Post by Camilia on 2009-10-09
I have no window software on my computer. I have only ubuntu. I followed the instructions, put the cd in and then opened the virtual box.

---

### Post by mechro on 2009-10-09
Have you installed Windows XP into Virtual Box using your Windows XP CD?

---

### Post by Camilia on 2009-10-09
> **mechro said:**
> Have you installed Windows XP into Virtual Box using your Windows XP CD?

No after some upgrades in ended up in accessories of ubuntu. Just followed the instructions.

Have you used virtual box from accessories?

---

### Post by UranUtan on 2009-10-09
> **Camilia said:**
> I followed the instruction to set up the virtual box.  Then inserted the CD. The result is not bootable media found. System halted. 

What can I do?

A VM needs to be prepared the same way than a physical machine. This means when you create a new VM, you need first to install the OS (WinXP in your case). Then probably you'll need to install Service Packs and run AutoUpdate. After that you will install the Windows applications in the VMs.

Sounds like you have a lot of concepts to get acquainted with. The best would be to read the Virtualbox manual entirely. There are a few key concepts you need to understand such as virtual hardware (ex: the network adapter, hard drive, video card are all virtualized). Then experiment, probably need some trials and errors . In case of questions go to Virtualbox forum and ask questions there.

When I started using with VM, I created / delete / re-create so many VMs before I got it right.

The cool things with VMs is that the physical CD/DVD is not needed. I always use ISO images.

Good lucks.

---

### Post by mechro on 2009-10-09
Sorry Camillia, but you're completely missing the point about Virtual Box.

Think of it as a brand new computer you have bought from a dealer, but in this case the dealer hasn't installed an operating system for you... you have to do that yourself by (in the case of Windows) purchasing a CD and installing it yourself.

Nice to talk to you; I've got to go now but I'd suggest looking at Wine or finding a computer with Windows on it.

---

### Post by Camilia on 2009-10-09
> **UranUtan said:**
> A VM needs to be prepared the same way than a physical machine. This means when you create a new VM, you need first to install the OS (WinXP in your case). Sounds like you have a lot of concepts to get acquainted with. The best would be to read the Virtualbox manual entirely


Now I am totally confused.  I thought the reason to use virtual box was to replace win xp os. I have wxp CD. I don't want any window software on my computer. People with wxp have had money stollen out of their bank accounts. There is a new invisible bug attaching to winxp.

Is there a manual on this site? I don't see 1. I tried to learn about virtual before I posted thread.

Where do find info to change CD to ISO image.

---

### Post by UranUtan on 2009-10-09
> **Camilia said:**
> Now I am totally confused.  I thought the reason to use virtual box was to replace win xp os.
...
Where do find info to change CD to ISO image.

Virtualbox doesn't replace WinXP. It help you to create an empty VM and you put whatever you want in it. Another user may want to use Virtualbox to run Linux. Actually that was what I did when I learnt Ubuntu (from WinXP I ran a Virtualbox VM that I installed Ubuntu inside). Or from Ubuntu I can run a VM with Windows 2003 64 bits instead of WinXP. I hope you see now the potential of a Virtual Machine. 

Virtualbox is just the name of a product (now owned by Oracle) that allows you to create and run VMs. Therefore to have the Virtualbox manual, you need to get it from Virtualbox website: [http://download.virtualbox.org/virtualbox/3.0.8/UserManual.pdf](http://download.virtualbox.org/virtualbox/3.0.8/UserManual.pdf)

To create an ISO image, the simplest is to use Brasero, make a copy CD or DVD and instead to selecting the DVD Writer, just select burn into ISO image. You will get more details by searching Google with keywords such as "create ISO image". You can get ISO from download, for example, Ubuntu can be downloaded as ISO images. All Microsoft products are available by ISO download. If what you have is a CD or DVD and you don't feel comfortable to create an ISO image, you can also configure Virtualbox to read the CD/DVD drive. Don't feel lost about this ISO stuff, this is just the "image" of the CD or DVD but saved in a file so that it can be copied or downloaded. Please read more from Internet searched to learn for more details.

> **Camilia said:**
> I don't want any window software on my computer.
I have switched my wife computer to Ubuntu, mainly because I had to do to much maintenance. But some Windows apps cannot be replaced easily. My wife absolutely needs Office 2007. For this Virtualbox is perfect. Conveniently I have just created a post in the forum to show how to create an UNHACKABLE WinXP virtual machine:

**The best Windows is XP without Internet access**
[http://ubuntuforums.org/showthread.php?t=1287238](http://ubuntuforums.org/showthread.php?t=1287238)

This could be useful for you later when you are familiar with Virtualbox.

---

