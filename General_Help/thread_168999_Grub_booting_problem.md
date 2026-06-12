---
title: "Grub booting problem"
date: 2006-05-01
forum: General Help
---

### Post by PaulL on 2006-05-01
I have built a new kernel (it's a long story) from source.
Everything appeared to go O.K. and I updated grub, which found both my new kernel (and of course the old one). I checked the menu.lst file and the root for both is (hd0,0), as I expect - there is no /boot partition. 
But when I try to boot using the new kernel I get a kernel panic 'unable to mount root fs on unknown-block (0,0)'. The old kernel obviously can mount O.K. The file system on the / partition is ext3 and this is built into the new kernel.

Any ideas?

---

### Post by geek.de.nz on 2006-05-02
Mmhh, weird. Should work if you compiled in ext3 support, but try passing a kernel parameter. Edit /boot/grub/menu.lst and append your root partition to the kernel as in:

```

title       Ubuntu, kernel 2.6.12-whatever
root        (hd0,0)
kernel      /vmlinuz root=/dev/hda1 ro quiet
savedefault
boot

```

the parameter 'root=/dev/hda1' depends on your setup, but it should be the same as before. Hope that helps. But since you're saying that you compiled your own kernel, you probably know that already.

Also, if you compile your own kernel, try to first use the Ubuntu patched kernel and use an old .config file and do 'make oldconfig'. I had lots of trouble like this with custom made 'vanilla' kernels that did not work on the distribution I was using.

By the way, are you by any chance lecturer at Massey, Palmerston North, NZ? If yes that would be quite funny, because I should really be working on an assignment that's due for that paper now, but I'm procrastenating by posting in these forums.

---

### Post by PaulL on 2006-05-02
It says all that already in my menu.lst file. 
I hoped that making an initrd file might help my case, but the mkinitrd package doesn't appear to exist on the Ubuntu repositries - has it been superseeded by something else? I suppose the original Ubuntu installation puts one in because somebody might want to use a wierd and wonderfull obscure filesystem which is only a module - but I _shouldn't _need one.
I initially tried a new kernel on a RAID system - carefully building in RAID support, when that didn't work I went back to a (new) ext3 file system thinking I'd been a bit ambitious, and now even this won't work. As I think I said earlier getting the sources  from the repositries doesn't get you a .config file - a pity it's always good to have somewhere to start.
No I'm not a lecturer - must be a different Paul (there are a few of us around)

---

### Post by PaulL on 2006-05-02
(Addendum to my last) I think this problem is spread over a couple of posts because I wanted to separate the problems, but I'll go away and try your .config advice,

---

### Post by geek.de.nz on 2006-05-02
Well, but there might not be as many Paul L.s around your age ;-).

Also try 

[http://www.ubuntuforums.org/showthread.php?t=56835&page=6#1](http://www.ubuntuforums.org/showthread.php?t=56835&page=6#1)

[http://ubuntuforums.org/showthread.php?t=75443&page=5&highlight=suspend2#1](http://ubuntuforums.org/showthread.php?t=75443&page=5&highlight=suspend2#1)


Worked for me. I especially like the suspend2 part. ;-)

---

### Post by PaulL on 2006-05-02
Well I found the config file and used it to build a 2.6.12 kernel with sources taken from kernel-tree. However make fails with 'Inconsistent kallsyms data'. So either the config is not quite correct or there is something wrong in kernel tree.
This is ridiculous - I've built kernels before and never come across this sort of thing.
Anyway I've come to the conclusion that Ubuntu seems to work quite well on a desktop system (as long as you always accept default options) but is a waste of time as a server. I'll go back to the original Mandrake setup and throw the Ubuntu disks away in case I'm ever tempted to put them in a cd drive again.

---

