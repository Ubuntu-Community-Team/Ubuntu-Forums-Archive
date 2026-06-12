---
title: "How to install Windows"
date: 2010-08-07
forum: General Help
---

### Post by maknib on 2010-08-07
Hi Guys,

I only have 1 partition on my PC and at the moment it is only running Ubuntu 10.4

i now have a xp cd but when i boot from it it gets to "Setup is starting windows" on the blue screen and won't go any further

is there something i need to do?

i want to put windows back on because i need Flash cs3 some games that dont run on ubuntu and Fruity loops

Or is there a way i  can make a partitin to try to install winows on it now?

im a real noob when it comes to this sort of stuff

thanks

---

### Post by Ozymandias_117 on 2010-08-07
> **maknib said:**
> Hi Guys,

I only have 1 partition on my PC and at the moment it is only running Ubuntu 10.4

i now have a xp cd but when i boot from it it gets to "Setup is starting windows" on the blue screen and won't go any further

is there something i need to do?

i want to put windows back on because i need Flash cs3 some games that dont run on ubuntu and Fruity loops

Or is there a way i  can make a partitin to try to install winows on it now?

im a real noob when it comes to this sort of stuff

thanks

It never gets to a screen asking about hard drives, and it never displays any errors?

---

### Post by bergfly on 2010-08-07
Depending on the spec of your box, you will either be able to run Windows in a virtual environment, or you will need to create some space on the hard disk to install it. I would definitely try the virtual option first. I have a 5 year old laptop that runs windows XP fine inside virtualbox. 

Go to your package manager and install Virtualbox OSE. Once that is installed, then simply create a new virtual machine. It will prompt you through step by step.

If this does not work, you will need to use Gparted to create a windows partition on the hard disk. The reason windows setup won't boot is it can't find a hard disk file system it recognizes in order to try to install on to. Hence you need to give it an NTFS partition to install into.

---

### Post by Ozymandias_117 on 2010-08-07
> **bergfly said:**
> Depending on the spec of your box, you will either be able to run Windows in a virtual environment, or you will need to create some space on the hard disk to install it. I would definitely try the virtual option first. I have a 5 year old laptop that runs windows XP fine inside virtualbox. 

Go to your package manager and install Virtualbox OSE. Once that is installed, then simply create a new virtual machine. It will prompt you through step by step.

If this does not work, you will need to use Gparted to create a windows partition on the hard disk. The reason windows setup won't boot is it can't find a hard disk file system it recognizes in order to try to install on to. Hence you need to give it an NTFS partition to install into.

I would advise going to Virtualbox's website and getting the proprietary one. You lose three or four features, including USB support, with the OSE (open-source edition).

---

### Post by maknib on 2010-08-07
> **bergfly said:**
> Depending on the spec of your box, you will either be able to run Windows in a virtual environment, or you will need to create some space on the hard disk to install it. I would definitely try the virtual option first. I have a 5 year old laptop that runs windows XP fine inside virtualbox. 

Go to your package manager and install Virtualbox OSE. Once that is installed, then simply create a new virtual machine. It will prompt you through step by step.

If this does not work, you will need to use Gparted to create a windows partition on the hard disk. The reason windows setup won't boot is it can't find a hard disk file system it recognizes in order to try to install on to. Hence you need to give it an NTFS partition to install into.

So does this virtualbox thing actually install windows? as in will windows run normally as if it is really installed?

---

### Post by worksofcraft on 2010-08-07
I advise buying a second hard drive.
Power off, disconnect your Ubuntu drive and plug in teh new drive. Power up and install Windows. Note you will need a legitimate Windows key to activate it.

Then power off again. Reconnect both your hard drives and make Ubuntu the primary drive. When it boots to Ubuntu, open a terminal and do following:

```

sudo update-grub

```

it will find your windows installation and add it to your boot menu so you can then choose whichever you want.

Ubuntu can mount the Windows NTFS drive and you can transfer files between them. You can even remove your Ubuntu drive and it will simply boot with standard Windows.

p.s. Virtualbox is good but not so good for games that demand high performance graphics cards.

---

### Post by maknib on 2010-08-07
> **worksofcraft said:**
> I advise buying a second hard drive.
Power off, disconnect your Ubuntu drive and plug in teh new drive. Power up and install Windows. Note you will need a legitimate Windows key to activate it.

Then power off again. Reconnect both your hard drives and make Ubuntu the primary drive. When it boots to Ubuntu, open a terminal and do following:

```

sudo update-grub

```

it will find your windows installation and add it to your boot menu so you can then choose whichever you want.

Ubuntu can mount the Windows NTFS drive and you can transfer files between them. You can even remove your Ubuntu drive and it will simply boot with standard Windows.

thanks i'm kinda broke right now so this virtualbox thing might be ok. i like Ubuntu alot but as long as this lets me run Flash and Fruity loops propperly i'll be happy

---

### Post by Ozymandias_117 on 2010-08-07
You would boot to ubuntu, then run Virtualbox. Windows would run as though it was a program in Ubuntu.

What exactly is on the screen when the Windows installer freezes?

---

### Post by bergfly on 2010-08-07
Once you have put windows in there, it runs normally within a window (or full screen if you prefer) Essentially it is running as a program within Ubuntu. As pointed out, the free version has some limitations on the hardware side. If you need to access hardware directly from Windows that is not networked (like a usb printer) you may have issues. However in terms of running games, this will be no problem. 

I run it at work on this old beast of a laptop to use outlook and connect to all manner of corporate devices without issue.

As said before, you do need the spec on the laptop. Ubuntu will be running all the time, using some resources. So windows will have less access to resources than it would if you booted into it natively.

---

### Post by maknib on 2010-08-07
> **Ozymandias_117 said:**
> You would boot to ubuntu, then run Virtualbox. Windows would run as though it was a program in Ubuntu.

What exactly is on the screen when the Windows installer freezes?

just a blue screen befopre it looks at patitions

---

### Post by maknib on 2010-08-07
> **bergfly said:**
> Once you have put windows in there, it runs normally within a window (or full screen if you prefer) Essentially it is running as a program within Ubuntu. As pointed out, the free version has some limitations on the hardware side. If you need to access hardware directly from Windows that is not networked (like a usb printer) you may have issues. However in terms of running games, this will be no problem. 

I run it at work on this old beast of a laptop to use outlook and connect to all manner of corporate devices without issue.

As said before, you do need the spec on the laptop. Ubuntu will be running all the time, using some resources. So windows will have less access to resources than it would if you booted into it natively.

yeah thanks, i wont need all that stuff i'd use ubuntu for that. just to run windows programs that wine can't is all im insterested in. i really actually dont want a full version of windows it's too much of a headtrip to keep protected and working

Love Ubuntu

oh and right now its formatting in my Virtualbox so this seems to be working :)

---

