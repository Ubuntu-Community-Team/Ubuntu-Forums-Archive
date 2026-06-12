---
title: "Help!!!!!!!!"
date: 2009-12-12
forum: General Help
---

### Post by wylekat on 2009-12-12
I updated Xubuntu last night, and then shut down the machine. I booted it tonight, and instead of it going to the usual menus, I get:

GNU Grub version 1.97 ~beta4
Minimal BASH-like blah blah blah..... 

And sh :grub>

I NEED Xubuntu to boot properly, as I have some 3d files that will take me somewhere around forever and ever to recreate. 

So...... HELP? :(

---

### Post by llamabr on 2009-12-12
Hi.  If you're unable to get in, eventually, you can use a livecd to access those files.

btw, you'll get better help with a more informative subject line.

---

### Post by wylekat on 2009-12-13
How do I do that with a live cd? Sorry about the thread title... Is there a way to change it?

---

### Post by wylekat on 2009-12-13
I fixed the thread title, and saved a copy of root.disk to a second drive. I am about ready to erase the old install, do the live cd and see what I can salvage from there.

And no. I do not have a freaking clue what I am doing.

---

### Post by Leppie on 2009-12-13
You most probably can still boot into xubuntu.
Issue the "ls /", this should show you where grub gets /boot from and then it shows the contents. If it doesn't give you the location of /boot, issue the command without the trailing slash. You can use ls for viewing directory listings as well.

Now to boot:
```
>set root=(hd0,Y)  ##most people have linux installed on /dev/sdaY, if this is different for you change accordingly
>linux /vmlinuz root=/dev/sdaY ro
>initrd /initrd.img
>boot
```

Once in ubuntu, update the grub configuration:
```
$sudo update-grub
```

---

