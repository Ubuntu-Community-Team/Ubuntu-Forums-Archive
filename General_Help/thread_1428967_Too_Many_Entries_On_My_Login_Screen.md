---
title: "Too Many Entries On My Login Screen"
date: 2010-03-13
forum: General Help
---

### Post by Don Cunningham on 2010-03-13
I dual boot with Ubuntu and Windows. Each time I run Update Manager it adds an entry to the boot screen pushing the Windows entry down a notch. 
I really only need the latest entry for Ubuntu and the Windows entry. Is there any way to remove the old ones?#-o

 drc

---

### Post by audiomick on 2010-03-13
Hallo.

Firstly, just so you know: A kernel update doesn't remove the old kernel. That is why your Grub menu is getting longer. It is not worrying in any way, just annoying.

Have a look here
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
The first section tells you how to just change the menu; further down there are instructions for actually removing the old kernels from the computer.

I haven't tried any of this myself, but the guide looks ok.

---

### Post by smerral on 2010-03-13
Well this is how I do it.

Open up a terminal and type:

sudo apt-get purge linux-image-2.6.31-19-generic (or whichever kernel you want to remove).

Then:

sudo update-grub

---

### Post by Don Cunningham on 2010-03-14
smerral,
  Thanks for the reply. When I tried that I got this message:

 Package linux-image is not installed, so not removed
E: Couldn't find package 2.6.31-19

  What am I doing wrong?

 drc

---

### Post by byStanderone on 2010-03-14
...you can also use synaptic manager by removing the old kernels that you'd want to take out...do a complete removal of the concerned kernels...and don't forget to sudo update-grub after the synaptic session.

---

### Post by audiomick on 2010-03-14
Read through the link I posted. There is an explanation of how to do that using the synaptic package manager down towards the bottom of the first post in the thread. It includes a way of looking for the exact names of the packages you want to remove. That is the problem you have right now: you have made some kind of typo in the command to de-install the kernel.

---

### Post by Don Cunningham on 2010-03-14
> **byStanderone said:**
> ...you can also use synaptic manager by removing the old kernels that you'd want to take out...do a complete removal of the concerned kernels...and don't forget to sudo update-grub after the synaptic session.

byStanderone and Michael,

  The synaptic manager worked! I'm not very good at using the terminal yet. I think I put a dot where a dash should be. Computers take things very literally.:p  Do I need to do the update grub if when I use package manager?
  Thank you for your help!

drc

---

### Post by audiomick on 2010-03-14
> **Don Cunningham said:**
> ...  Do I need to do the update grub if when I use package manager?
That's a bit hard to say. The guide in the link implies that you don't, but then refers to "menu.lst" in connection with that. That file is from grub legacy, and you have grub2, which uses a different file.

I assume that you don't have to, but don't know for sure.
You have two choices:
Do nothing and re-boot. If the removed kernels are gone, all is well. If they are still in the list you know you need to run
```
sudo update-grub
```Note: if you try and boot to an older kernel that is still in the list but not there anymore, I think grub will get terribly confused and make trouble, so don't fall for the temptation of doing that to check if the old kernels are really gone...

Run
```
sudo update-grub
```now just to be sure. This shouldn't hurt anything, and will make sure that the grub menu only shows the kernels that are really there. The disadvantage is that the next time you remove old kernels, you still wont know if the menu gets updated automatically or not...

---

### Post by Don Cunningham on 2010-03-14
Michael,
  They are gone without running update. Again, thanks very much!
drc

---

### Post by audiomick on 2010-03-14
Thanks for letting me know.

---

### Post by rahilm on 2010-03-14
i heard sudo apt-get autoremove also gets rid of outdated kernels..

---

