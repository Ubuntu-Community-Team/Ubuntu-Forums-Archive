---
title: "Change Ubuntu partition size."
date: 2011-02-26
forum: General Help
---

### Post by Engammalsko on 2011-02-26
Hi, I have gparted but can't change my ubuntu partition.
I guess that's because I can't unmount it. And... I guess my Ubuntu won't work if I unmount it? xD

So... I heard that I could use a Gparted live CD to do this.
The only problem is that I can't boot from a cd/dvd drive.

So, is there a option to change the partition size while running Ubuntu?
Or is there a option to somehow unlock all BIOS settings?

When I try to acess the BIOS settings it ask for a password, and I just press enter... And I come to a menu where I can't change anything. Is this because of wrong password? Or is the password right but everything is blocked?

I mean, I can't change boot priotiy to cd/dvd just HDD and LAN.
So please help me.

---

### Post by Quackers on 2011-02-26
How did you install Ubuntu? Did you use a Live usb? If so, boot from that and select "try ubuntu" then when the desktop loads use gparted. That way the system is not mounted.

---

### Post by runeh76 on 2011-02-26
Hi

There is also **KDE Partition Manager** install&try it.
U could also test, if u can launch gparted or KDE partition from root terminal in rescue-mode. 
Boot PC and keep hitting ESC, so u can choose rescue-mode

---

### Post by Engammalsko on 2011-02-26
I installed Ubuntu by taking out my HDD and installed Ubuntu on my HDD with my math teacher's computer xD

My school have blocked all BIOS settings, can't boot from USB or External drive etc. ONLY the computers HDD and LAN.
Btw, my math teacher is not from my school... xD

---

### Post by Engammalsko on 2011-02-26
Nopp, KDE partitionmanager doesn't work.
I can't change anything when Ubuntu is running. It needs to be unmounted.
I guess this will work if I install Windows...

But... I can't do that without booting from cd. So that's sucks.

And Clonening my Ubuntu wouldn't help since I can't reinstall it without help of another laptop...

But I'll try the esc thingy. Sure it is esc on all computer? Well. I write back for the results.

---

### Post by Quackers on 2011-02-26
It may be the shift key that you need to press. It depends on which version of Ubuntu you are using.

---

### Post by gsgleason on 2011-02-26
Perhaps you should research how to recover your bios password.  Maybe you need to remove the internal battery or pull a jumper or something.

---

### Post by Hedgehog1 on 2011-02-26
> **Engammalsko said:**
> I installed Ubuntu by taking out my HDD and installed Ubuntu on my HDD with my math teacher's computer xD

My school have blocked all BIOS settings, can't boot from USB or External drive etc. ONLY the computers HDD and LAN.
Btw, my math teacher is not from my school... xD

Your school, like the IT department at my work, doesn't want folks doing the very thing you are trying to do.  This is why they have put passwords on the bios.

Your solution to remove the drive and load Ubuntu on it was a way to bypass that very security.  Without the ability to alter your boot order or select a one-time boot order, you are stuck taking the drive to another system and resizing using Gparted off a LiveCD.

I should add, you are not supposed to do this.  Just as I was not supposed to dual boot Ubuntu at work either.  I only got caught because I could not run the FIXMBR when I removed the dual boot later - I didn't know the extra admin password they had added (and I got scolded).

:KS

---

### Post by Engammalsko on 2011-02-26
Yeah but... When xp crash. And you are not even able to boot it... What should you do?
It's my vocation and i NEEDED a computer.
Well, I can still install a new xp with help of another computer. Which I will do as soon as my vocation is over.
And actually... I haven't get caught yet. I login as admin all the time :p

And the ones that got caught (which I assume I'll get soon) only got thier os reinstalled... So, in worst case, I need to do a backup.

---

### Post by Engammalsko on 2011-02-26
> **Quackers said:**
> It may be the shift key that you need to press. It depends on which version of Ubuntu you are using.

10.10

I can also acess covery mode by pressing Down then Enter.
Ubuntu starts up with the terminal and ask me for the username/password.

Can I boot the cd from there with a normal terminal command?

---

