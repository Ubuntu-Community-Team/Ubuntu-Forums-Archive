---
title: "dos"
date: 2010-11-17
forum: General Help
---

### Post by mr.farenheit on 2010-11-17
i love dos. i use freedos. i wanna dual boot ubuntu with freedos but i have a few concerns. my main fear is either having the install go bad and mess up grub or have grub not recognize the partition. i'm also afraid of it messing up anything with my win7 partition. its only gonna be a small sized partition around 6 gb at the most. has anyone had an experience with this and is so can they point me out to the better outcome?

---

### Post by io5cml4z on 2010-11-17
> **mr.farenheit said:**
> i love dos. i use freedos. i wanna dual boot ubuntu with freedos but i have a few concerns. my main fear is either having the install go bad and mess up grub or have grub not recognize the partition. i'm also afraid of it messing up anything with my win7 partition. its only gonna be a small sized partition around 6 gb at the most. has anyone had an experience with this and is so can they point me out to the better outcome?

It should work fine. Install Ubuntu alongside the other operating systems (in the setup). Also, if like me, you can't find that option, you may have to create a new partition. Make it big enough for all of your Ubuntu-related things (e.g. Swap, File system, etc.), and then just install Ubuntu. Piece of cake. :popcorn:
Edit: About the grub part, don't worry about it, unless you do something stupid and accidentally format the boot partition (I did that once, had to reinstall, but my Windows partition was completely fine).

---

### Post by matt_symes on 2010-11-17
Hi

If there are any problems with grub just keep your live CD handy and a  whole bunch of people here can help you out so don't worry. Make sure you  have had a good play with the LiveCD as this can help identify any  hardware issues. 

Shrink your windows partition with the windows tools, if you need to shrink it. This is important.

Kind regards

---

### Post by SeijiSensei on 2010-11-17
You can also run DOS programs using dosemu.  It basically a virtual machine that runs only DOS.  Just install with "sudo apt-get install dosemu" then run "dosemu &" at the prompt.

---

### Post by mr.farenheit on 2010-11-27
dosemu works good. still gonna try shrinking windows to make an actual dos install though, thanks gang!:lolflag:

---

