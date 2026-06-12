---
title: "Massive iPod failure help"
date: 2011-04-04
forum: General Help
---

### Post by Spyderkid on 2011-04-04
I have had a massive bugger up with my iPod Touch 4th Generation, I accidentally formatted it!!! Don't ask me how I managed it but I just have.

So now it doesn't mount.

however if i run lsusb it is there?!?!

what shall i do?


Thanks! 
Help appreaciated...

---

### Post by Chronon on 2011-04-04
Put it into Disk Mode and use iTunes to Restore it.

Alternatively, there are instructions for restoring from Linux here:
[http://www.rockbox.org/wiki/IpodManualRestore](http://www.rockbox.org/wiki/IpodManualRestore)

---

### Post by wolfen69 on 2011-04-04
> **Chronon said:**
> Put it into Disk Mode and use iTunes to Restore it.

Alternatively, there are instructions for restoring from Linux here:
[http://www.rockbox.org/wiki/IpodManualRestore](http://www.rockbox.org/wiki/IpodManualRestore)

Thanks for that link, didn't know that could be done. But for some people, it may just be easier to find a ubiquitous windows machine, and use itunes to restore. But it's good to know it's possible without itunes.

---

### Post by Spyderkid on 2011-04-04
I'm not quite sure if you understand I can't put the iPod into to iTunes because theres no software or files on the iPod to say its an iPod.

To the computer it's just an 8GB HardDisk.

What i need are those files that say its an iPod

---

### Post by Spyderkid on 2011-04-04
And also the link you posted doesn't have a thing for the iPod touch 4gen. 

(sorry key piece of information missing there)

---

### Post by Chronon on 2011-04-04
Ah.  It's not one of the models that has a (UMS) Disk Mode stored in flash ROM.  In that case, you should try to put it into DFU mode and use iTunes to restore it.

There are various pages describing how to get into DFU mode.

---

### Post by Spyderkid on 2011-04-05
Ah no it does have the little bit of software is on there. SORRY.

However it doesn't mount????

it does show up when i run lsusb though.

---

### Post by Chronon on 2011-04-07
I believe that DFU mode is from code stored in a ROM of some sort.  According to my understanding, formatting the drive shouldn't affect this functionality.

---

### Post by linuxuser12345 on 2011-04-07
You *have* to use iTunes to reimage your iPod easily, and iTunes doesn't work correctly under Wine in Linux. I would suggest using a friend's Mac or Windows PC real quick to quickly reimage your iPod.

I had to do the same thing, so *I know*! :P

---

### Post by Spyderkid on 2011-04-08
Windows 7 found a driver for the "apple USB" (which was my ipod) automaticly and then i used iTunes to restore my iPod in iTunes recovery mode.

I do have to say you can't critisize Windows7 functionality

---

