---
title: "My last post and running Ubuntu virtually"
date: 2010-11-15
forum: General Help
---

### Post by Ledus on 2010-11-15
Quite a long time ago i made a post about how to run ubuntu virtually while running xp or whatever.

I dont remember exactly what i did so is there anyway i could find this post?(the post could very well be last year)

All I do remember is that i used a virtual booting program by Sun Microsystems(cant remember the name)

Also i was using a different OS and a different compute so here are my specs.

OS: Windows 7 home prem
Graphics card: GT 240 GDDR3 1gb
Processor: AMD Athlon II X4 635 (4 cores @ 2.9ghz) 
Ram: 3gb DDR3

Is that enough?

---

### Post by drs305 on 2010-11-15
Is this the one you are looking for?
[http://ubuntuforums.org/showthread.php?t=1397942]("http://ubuntuforums.org/showthread.php?t=1397942")

You can click on your name in the left pane of a post and click on "find more posts by"

---

### Post by blur xc on 2010-11-15
> **Ledus said:**
> Quite a long time ago i made a post about how to run ubuntu virtually while running xp or whatever.

I dont remember exactly what i did so is there anyway i could find this post?(the post could very well be last year)

All I do remember is that i used a virtual booting program by Sun Microsystems(cant remember the name)

Also i was using a different OS and a different compute so here are my specs.

OS: Windows 7 home prem
Graphics card: GT 240 GDDR3 1gb
Processor: AMD Athlon II X4 635 (4 cores @ 2.9ghz) 
Ram: 3gb DDR3

Is that enough?

Sun was bought by oracle so now it's Oracle VirtualBox.  Go the the Oracle website, install vbox, and read it's documentation (it's pretty good) on how to create a virtual hard drive, and install an os on it.  After that you need to install the guest additions to enable usb ports, full res graphics, shared folders, etc...  I'm posting this from Ubuntu 10.04 running in vbox on a Win7 host right now.

BM

---

### Post by Ledus on 2010-11-15
I know how to do it now but theres just one problem now.

I know my OS is 64 bit(system infomation), i downloaded  the 64 bit iso image of ubuntu however after i set everything and V-box ask's me to give the media source and tries to load up it says error and that it needs a 86-64 bit cpu while it only dected that i have a i686 CPU

and also will Oracle v-box uninstall everything it installed if i uninstall it? (networks software devices..)

---

### Post by blur xc on 2010-11-15
> **Ledus said:**
> I know how to do it now but theres just one problem now.

I know my OS is 64 bit(system infomation), i downloaded  the 64 bit iso image of ubuntu however after i set everything and V-box ask's me to give the media source and tries to load up it says error and that it needs a 86-64 bit cpu while it only dected that i have a i686 CPU

I have a vague recollection of this - I think there *might* be some obscure virtualization setting in your motherboard's bios that lets you run a 64bit guest os.  I guess that kind of depends on how modern of a cpu you have..  If you are running 64bit Win7 on it, I can't image it can be that old... 

And I am running 64bit ubunut as a guest over here, on my intel core 2 extreme (woo hoo!!) cpu..

Anyway, give it a look see.

BM

---

### Post by Ledus on 2010-11-15
> **blur xc said:**
> I have a vague recollection of this - I think there *might* be some obscure virtualization setting in your motherboard's bios that lets you run a 64bit guest os.  I guess that kind of depends on how modern of a cpu you have..  If you are running 64bit Win7 on it, I can't image it can be that old... 

And I am running 64bit ubunut as a guest over here, on my intel core 2 extreme (woo hoo!!) cpu..

Anyway, give it a look see.

BM


It's release date was March 2010, doesnt seem that long now does it?

anyway i think i'll just try it on a usb drive =/

Now i deleted the VM(not the v-box, just the ubutu vm) but how do i delete the virtual hard drive and also if i uninstall oracle, will it uninstall everying it installed such as virtual network devices?

---

### Post by Ledus on 2010-11-15
I mean i think its...

1) got to Virtual media manager
2) select the virtual hard drive
3) click remove

?

---

