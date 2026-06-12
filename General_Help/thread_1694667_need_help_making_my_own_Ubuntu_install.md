---
title: "need help making my own Ubuntu install"
date: 2011-02-24
forum: General Help
---

### Post by TAYLOR1337 on 2011-02-24
i was wondering how i could go about making my own Ubuntu installation where a few things are already pre-installed, and i wont have to go to the package manager to install. (mainly stuff like Flash & skype)

i want to do this mainly cus i wanted to send a usb stick off (she has a net-book with no CD-drive) with ubuntu on it and all to my fiancé in the states, but as she isn't as techy when it comes to computers, i wanted it with everything pre-installed right out of the box.

anyone know how i can do this or could help me with this?

Thanks

(sorry if i'm posting this in the wrong category)

---

### Post by violinuxer on 2011-02-24
Welcome to the forums :)

I have tried to do the same thing. Your best bet would be to try the Ubuntu Customization Kit. (package name uck) It takes a normal Ubuntu image and lets you operate a package manager on it (Synaptic) Any packages you install become part of the final image. However,  you might need to use UNetbootin to put the final image on your flash drive, as, in my experience, the standard flash drive software does not accept non-standard images.

Another one that might be worth googling is Remastersys. I have not had much experience with it, but that might work too.

Anyhow, best of luck!

violinuxer

---

### Post by jazzerit on 2011-02-24
you could also install a copy of ubuntu in virtualbox, then configure it, the use remastersys to make an iso, then either move it out with a usb stick (needs non-open source edition) or similar, or ssh (need to have an ssh server set up).

---

### Post by violinuxer on 2011-02-24
I might ask- when you install from a live usb, are all programs that are installed using on the usb drive on the machine? It wouldn't make any sense to spend all the time customizing when those programs won't get installed when you install to the hard disk.

*If* the programs do get installed, somebody could make a normal USB drive with persistence then install the programs they needed and then have the other person do a normal install. Supposedly the programs they wanted would get installed as well.

Worth a thought.....

violinuxer

---

