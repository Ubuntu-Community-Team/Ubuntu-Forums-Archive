---
title: "Grub rescue help"
date: 2010-02-27
forum: General Help
---

### Post by nathbfreak on 2010-02-27
I installed "Karmic" two days ago. Today, I decided to mount my c:\ drive from windows and copy important files and then
 delete partiition I suceeding in this task and then expanded the ubuntu partition. Then I noticed Gparted said my hard drive was empty and I couldn't open any programs or folders so I restarted my computer only to have grub say this:
 
GRUB loading.
error: no such partition
grub rescue>
 
Do boot from the LiveCD or what do I type to bypass this?
Can I just reinstall ubuntu and this promblem is fixed?
 
On my third day of Ubuntu and I break it.

---

### Post by johngreth on 2010-02-27
I'm not sure exactly what happened, but my guess based on what you described is that you accidentally deleted the Ubuntu partition instead of the windows partition. Since grub did load, the drive is still in tact, but the fact that it can't find the (Ubuntu) partition...

You could try typing the following commands into the grub prompt. This might be able to boot windows (or maybe Ubuntu if that's still there)...
```
root(hd0,0)
makeactive
chainloader + 1
boot
```

I guess the easiest way to fix this would be to just try to install Ubuntu again. If you had data thats gone and that you really need, you could look into getting a partition recovery tool.

If you do get into Ubuntu, there might be a complicated way to fix it without doing a fresh install, but installing Ubuntu is so easy, why bother?

---

### Post by sameer.walgude on 2010-03-12
Try this:

If you cannot go to normal grub mode, do this....

grub rescue> set prefix=(hd0,x)/boot/grub
grub rescue> insmod (hd0,x)/boot/grub/normal.mod
rescue:grub> normal


If still fails...boot up live cd...

at terminal...
sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub /dev/sda

substitute /media/{kubuntu9.10partition} with actual partition :)

If you get error message,(mapping fails), do this..

sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub -m 
/media/{kubuntu9.10partition}/boot/grub/device.map /dev/sda

All the best!

Thanks & Regards
Sameer J Walgude
[email]sameer.walgude@aol.in[/email]
+91 98191 15533

---

### Post by pritam_par on 2011-08-10
Try this it is solved here

[http://ubuntuforums.org/showthread.php?t=1485445](http://ubuntuforums.org/showthread.php?t=1485445)

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
________________________________________________

---

### Post by Andrew_nuts on 2012-01-16
> **pritam_par said:**
> Try this it is solved here

[http://ubuntuforums.org/showthread.php?t=1485445](http://ubuntuforums.org/showthread.php?t=1485445)

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
________________________________________________


Thanks for the above links just want to add that the solution on second link ,i.e [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) is again recommending  to another blog .ie
 [COLOR=darkred]**For an easy-to-understand summary including graphics,  the following site does a very good job - complete with  illustrations:**[/COLOR]
[http://opensource-sidh.blogspot.com/...ubuntu-cd.html]("http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html")  for grub rescue. 

I am new to Ubuntu and faces this problem and now its running smoothly. Thanks for the solution pritam

---

