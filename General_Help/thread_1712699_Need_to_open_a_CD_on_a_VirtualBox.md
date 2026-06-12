---
title: "Need to open a CD on a VirtualBox"
date: 2011-03-23
forum: General Help
---

### Post by Julian Luna on 2011-03-23
Ok here goes another noob problem
So I made a windows 7 virtual machine
But graphics run like crap
I need to install my motherboard's driver on that virtual machine
But since the virtual machine was created from an iso which was sorted into the CD/DVD device as an iso image; whenever I open the CD device from the virtual machine; it runs the win7 installer
So basically I need one of two things:
The virtual machine to recognize if I insert a CD on my CD/DVD hardware
Or to record the .iso image from my motherboard's cd (Which I don't know how to do so)
And sort it into the CD/DVD zone of the VirtualBox.

I need to install it because I can't even play chesstitans on there. It prompts me some window that tells me that I need Direct3D so basically I need to configure my [attached] graphic card which is pretty good it can run pretty well I just need to configure the motherboard's drivers or... something

Thanks people. Ubuntu's comunity is lovely.

Edit: Hope it's my graphics too, but things go too slow when the virtual machine is up. I probably need more ram or configure the virtual machine to use my rams instead of my hard disk, I'm not even sure if it's using the hard disk or not but I guess so cause everything goes really slow in there. Well not slow as fuq but mmm mouse freezes and teleports suddenly a lilbit. Anyways if you lead me to fix my Ram's usage and setting up my motherboard's drivers on this virtual machine i'm pretty sure it's gonna work

I think it's important to say ubuntu is x64 and win7 is x64 actually my processor is a dual core so the architecture supports it but I don't know if i'm actually asking it to go on x128 :s (It might be an stupid thought of me)

Ty

---

### Post by kelvin spratt on 2011-03-23
> **Julian Luna said:**
> Ok here goes another noob problem
So I made a windows 7 virtual machine
But graphics run like crap
I need to install my motherboard's driver on that virtual machine
But since the virtual machine was created from an iso which was sorted into the CD/DVD device as an iso image; whenever I open the CD device from the virtual machine; it runs the win7 installer
So basically I need one of two things:
The virtual machine to recognize if I insert a CD on my CD/DVD hardware
Or to record the .iso image from my motherboard's cd (Which I don't know how to do so)
And sort it into the CD/DVD zone of the VirtualBox.

I need to install it because I can't even play chesstitans on there. It prompts me some window that tells me that I need Direct3D so basically I need to configure my [attached] graphic card which is pretty good it can run pretty well I just need to configure the motherboard's drivers or... something

Thanks people. Ubuntu's comunity is lovely.

Edit: Hope it's my graphics too, but things go too slow when the virtual machine is up. I probably need more ram or configure the virtual machine to use my rams instead of my hard disk, I'm not even sure if it's using the hard disk or not but I guess so cause everything goes really slow in there. Well not slow as fuq but mmm mouse freezes and teleports suddenly a lilbit. Anyways if you lead me to fix my Ram's usage and setting up my motherboard's drivers on this virtual machine i'm pretty sure it's gonna work

I think it's important to say ubuntu is x64 and win7 is x64 actually my processor is a dual core so the architecture supports it but I don't know if i'm actually asking it to go on x128 :s (It might be an stupid thought of me)

Ty
You can't install the motherboard drivers in a virtual machine, as its running through a host which is using the correct drivers.
Virtual box uses its own drivers you need to install Guest additions + win7 can be very sluggish in v/box XP runs a lot better

---

### Post by jerome1232 on 2011-03-23
So yeah echo'ing from the above post, virtualization is very taxing on your computer.

Your computer is emulating alot of hardware, 3d graphics support is experimental in virtualbox and it will go slow. 


How much physical ram do you have on your host machine and how much have you allocated to your virtual machine?

Have you allowed the guest machine direct access to your video card? Try going into the settings for your virtual machine, going to display and checking "enable 3d acceleration"

Give it more ram. ram is good, more ram! I give my xp machine 256 MB's of ram and it runs well on that, you might need up to 1 GB for a win 7 guest, you shouldn't allocate much more than 50% of your real ram to a guest or your host's performance will suffer.

---

### Post by Julian Luna on 2011-03-23
Ok i'm gonna try to install XP
Jerome, my cpu's ram is 2 gygas, with 600 mb of swap space, and on Base Memory of my virtual machine it says 512 mb, video memory also says 16mb... is there a way I can change it? :] 

I enabled now 3d acceleration and 2d video acceleration. Modified the 16 mb video memory to 50 mb :] Now I'll run it and tell you how it goes, i'll modify my 512 base memory to 1 giga btw... [... Testing ...]

1.- I were adviced it's not good to set more than the 50% of my total cpu's ram so I set 828mb
2.- Still runs slow
[COLOR=Red]3.- Opened ChessTitans and it prompts me the same error about "Acceleration by hardware is not activated"[/COLOR]

Add: Do I need to install an antivirus if i'm using windows just as a virtual machine?
New: It's running a lil bit faster but it still have several graphical problems (I'm downloading the windows update's instalations)

---

### Post by Julian Luna on 2011-03-25
Bump D:

---

### Post by SeijiSensei on 2011-03-25
> **Julian Luna said:**
> [COLOR=Red]3.- Opened ChessTitans and it prompts me the same error about "Acceleration by hardware is not activated"[/COLOR]

I'll repeat what others have said already.  The OS inside a VirtualBox cannot address the video hardware directly.  VB provides an emulated video adapter to the guest operating system.  So enabling hardware acceleration on the video card is Ubuntu is all well and good, but that will only help programs running natively in Ubuntu.  Your VB guest can't see nor manipulate your actual video adapter.

I have a machine with 4 GB and allocate 1.5 GB to VirtualBox for my Win7 guest.  While the VB application will complain if you allocate more than 50% of your RAM to the guest, with Ubuntu as the host you can still give that much, or perhaps even a bit more, to Win7.  With 2 GB of memory, I'd try allocating 1280 MB to the Windows guest and leave Ubuntu with 768 MB or so.  If this slows down the Ubuntu desktop environment, and you can't afford to buy more RAM, then try turning off any "desktop effects" or replacing GNOME or KDE with a more lightweight desktop environment like [LXDE]("http://www.lxde.org/").

---

