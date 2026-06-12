---
title: "Removing Selections from GRUB"
date: 2010-02-06
forum: General Help
---

### Post by igriego on 2010-02-06
When i boot I'm prompted with several choices of different kernels and windows and another operating system I don't ever use how can I get rid of those?

---

### Post by brianfactors on 2010-02-06
All of grub's files are in /boot/grub/

I'm not in Ubuntu right now, but I think what you need to edit is the menu.list file (you'll need to have root privileges).

You can turn entries you don't want into comments with the pound sign if I remember correctly (#), but it should be pretty obvious once you open that file.

---

### Post by wangsuda on 2010-02-07
> **igriego said:**
> When i boot I'm prompted with several choices of different kernels and windows and another operating system I don't ever use how can I get rid of those?Removing old kernals is easy! Forst, find out which kernal you are using now. If you've done the latest update, then your kernal should be 2.6.31-19. All other kernals are old and can safely be removed. Here's how to do that:

1. Open Synaptic and click on the "Installed" option on your left.

2. In the search box, type in the kernal number you want to remove. MAKE SURE IT IS NOT YOUR CURRENT KERNAL!

3. Mark the old kernal elements for removal.

4. Click on apply.

You can also check out this thread [http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521) and specifically this post [http://ubuntuforums.org/showpost.php?p=8057950&postcount=8](http://ubuntuforums.org/showpost.php?p=8057950&postcount=8) for more detailed information.

---

### Post by igriego on 2010-02-07
Is there a command to find my kernel will I know there is but my UnixI class has been so long ago

---

### Post by igriego on 2010-02-07
Ok I got it as uname -r but it shows 2.6.28-14-generic and all the ones in Synaptic are 2.6.31-15? I can't even find the 2.6.28.XX

---

### Post by igriego on 2010-02-07
Another question do I want to remove the headers or the image?

---

### Post by igriego on 2010-02-07
Oh I found my kernel.

---

### Post by wangsuda on 2010-02-07
> **igriego said:**
> Another question do I want to remove the headers or the image?
Me personally, I usually remove everything. With that said, here's my set-up - I keep my original kernel, just in case I make a mistake. I then remove everything for all the kernels I don't use. Then I reboot. If everything goes well, I boot into my newest kernel with no problem. If it doesn't, I still have my original kernal to use in order to fix things.

---

### Post by igriego on 2010-02-07
I rebooted my computer without changing anything either in synaptic or the /boot and the latest kernel(2.6.31-19) is not given as a choice how do I make sure that is given as a choice?

---

### Post by kuin on 2010-02-07
the grub menu can find in grub/grub.cfg for ubuntu 9.10. or in grub/menu.lst for ubuntu 8.10. make sure, before you make change this file, you must backup it first.

---

### Post by igriego on 2010-02-07
I don't see the grub.cfg file but I changed the menu.lst file

---

### Post by igriego on 2010-02-07
I've found part of the problem the /boot/grub/menu.lst on my Ubuntu partition is not being read it is another operating system on the same drive, my question now is if I remove this partition will it boot my /boot/grub/menu.lst?

---

### Post by igriego on 2010-02-07
Or should I just copy and move my menu.lst from the partition I want it to be read to the partition that is actually getting read, but this just seems wrong to me.

---

### Post by igriego on 2010-02-07
Marking this as solved because menu.lst and grub.cfg were the files I needed to edit. Starting new thread for my other questions.

---

### Post by brianfactors on 2010-02-23
Wait! Hold it there. I think I told you wrong:

> Unlike Grub Legacy's *menu.lst* file, *grub.cfg* is NOT MEANT TO BE EDITED!!!"
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)


According to this documentation, for GRUB 2 you are supposed to edit[B]:
[/B]
**```
/etc/default/grub
```**

and then run

```
update-grub
```

Not edit grub.cfg. Sorry that I gave some incorrect info there.

---

### Post by brianfactors on 2010-03-18
wangsuda had the best advice. Just a couple things to add:

1) I didn't completely remove, so the vmlinuz and initrd files for the old kernels were still there. Grub still thought those kernel headers existed.

2) You can remove them using a command like
```
 sudo rm /boot/*-2.6.31-14-* 
```
If version 2.6.31-14 is the version you are trying to remove. Or you could just mv them somewhere else if you're a little scared of the irreversible nature of rm.
```
 sudo mv /boot/*-2.6.31-14-* ~
```

3) After you do this, be sure to run
```
update-grub
```
And then you're good.

But then again, you may not have to do this if you just click "completely remove."

---

