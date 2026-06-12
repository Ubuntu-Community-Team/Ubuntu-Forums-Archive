---
title: "Running Ubuntu 9.04 under Windows."
date: 2009-07-30
forum: General Help
---

### Post by ..::| Dave89 |::.. on 2009-07-30
I'm new to this forum, and not sure if this is the right place to ask, excuse me if it isn't. I came across an ISO image of Ubuntu 9.04 on a DVD that came with a PC magazine. I've always been interested in Linux, but never tried Ubuntu before. I managed to get it booted off a USB key with the help of an article in said magazine, but I want the ability to run it alongside Windows Vista the same way I do with the classic Mac OS, I've heard of VMware, but I believe that is a commercial product. Is there a free alternative that has networking capabilities?

TIA

Dave
Australia

---

### Post by howefield on 2009-07-30
> **..::| Dave89 |::.. said:**
> ... Is there a free alternative that has networking capabilities?

Virtualbox

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by Coding Monkey on 2009-07-30
You could also set up your system to dual boot.  This isn't too hard to accomplish; just google for a guide.  I prefer this approach, because you can have all your resources allocated to whichever OS you are on at a time, instead of having to run two OS's at once.

---

### Post by Monotoko on 2009-07-30
or for a completly hassle-free installation, just insert the disk while your in Windows and choose the "Install Inside Windows" option ;)

---

### Post by ..::| Dave89 |::.. on 2009-07-30
I got everything running under VirtualBox, all installed and working, including the networking. Only thing is, the max resolution it allows me is 800x600, any way to increase that?

Dave
Australia

---

### Post by Monotoko on 2009-07-30
Use the virtualbox additions, there should be an option for it under one of the menu's, then the .sh file on the new virtualdiskdrive :)

(this will allow your ubuntu to go to whatever size you want it, even full screen, and also some other cool features such as file sharing+USB sharing)

---

### Post by rannable on 2009-07-30
My recommendation is Virtualbox, its free and simple! (and stable too)

---

### Post by ..::| Dave89 |::.. on 2009-07-30
I'm not sure what VirtualBox Additions are.

Dave
Australia

---

### Post by howefield on 2009-07-30
Guest Additions is what they are, fourth or so paragraph down.

[http://www.virtualbox.org/wiki/VirtualBox](http://www.virtualbox.org/wiki/VirtualBox)

This gives you extra features, like resizing the guest window and improving performance.

From the devices menu, select Install Guest Additions.

---

### Post by JOKER__95 on 2009-07-30
insert the disk while your in Windows and choose the "Install Inside Windows" option
then when you reboot you will have the option to choose vista or ubuntu

---

### Post by hibliss on 2009-07-30
Why are you explaining how to install via Wubi when the OP already decided to use VirtualBox?

---

### Post by ..::| Dave89 |::.. on 2009-07-30
OK, I have it all up and running the way I wanted it. I'm typing from Ubuntu now. A couple more questions, how do I install applications, and how do I share file between host and guest OS?


Dave
Asutralia

---

### Post by howefield on 2009-07-30
System > Administration > Synaptic Package Manager

Search for program you want., and mark for installation by checking the box to the left of it. Then click apply, and apply again (you may be asked depending on the program to install dependancies, extra files required by the program in order to run).

You can also use the command line in terminal eg,

```
sudo apt-get install nameofprogram
```

To share folders between guest and host, set the relevant folders up in the Virtualbox settings for your vm. I'm guessing that you will be able to navigate to the folder via the places > network menu. (I only use windows guests with Linux hosts, and the shared folders appear in Windows Explorer in network.

Full virtualbox manual here

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

