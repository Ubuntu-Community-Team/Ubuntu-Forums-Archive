---
title: "Why is this here?"
date: 2009-09-04
forum: General Help
---

### Post by mayagrafix on 2009-09-04
Is the syslinux folder on my Windows C:\ drive left over from using the Ubuntu live CD? maybe leftover from installation? (I have Ubuntu installed on a separate second HD) the folder in question is outlined in red and contents are in right hand pane of pix.

[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/sislinuxSC.jpg[/IMG]

I would like to delete it if it is of no consequence.

Thanks for all the great help; Ubuntu Forum people, u are great!

---

### Post by Kristofer Van Orton on 2009-09-04
Well how big is the folder?
it might have something to do with the linux kernel and deleting it might make ubuntu or whatever linux distro not work
but i cant be sure im still kind of a noob to this :P
just trying to help

---

### Post by Japjeev on 2009-09-04
> **mayagrafix said:**
> Is the syslinux folder on my Windows C:\ drive left over from using the Ubuntu live CD? maybe leftover from installation? (I have Ubuntu installed on a separate second HD) the folder in question is outlined in red and contents are in right hand pane of pix.

[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/sislinuxSC.jpg[/IMG]

I would like to delete it if it is of no consequence.

Thanks for all the great help; Ubuntu Forum people, u are great!

whats discovery xp?

---

### Post by CatKiller on 2009-09-04
> **mayagrafix said:**
> I would like to delete it if it is of no consequence.

I shouldn't imagine that it's used by anything. Rename it to something else, and then, if something does suddenly break, you can rename it back again. If nothing breaks, you'll know that you can delete it.

---

### Post by P4man on 2009-09-04
what does the readme say ? :)

Im guessing its a left over from an attempt to make a bootable stick or something?

---

### Post by Nepherte on 2009-09-04
It's used as a boat loader: [http://en.wikipedia.org/wiki/SYSLINUX](http://en.wikipedia.org/wiki/SYSLINUX). I suggest you keep it unless you don't want to be able to boot your computer.

---

### Post by running_rabbit07 on 2009-09-04
> **Nepherte said:**
> It's used as a boat loader: [http://en.wikipedia.org/wiki/SYSLINUX](http://en.wikipedia.org/wiki/SYSLINUX). I suggest you keep it unless you don't want to be able to boot your computer.
+1 Make it hidden and never look at it again.

---

### Post by mayagrafix on 2009-09-06
> **Japjeev said:**
> whats discovery xp?
A second partition for Win XP on HD #1 (main partition has Vista)

Ubuntu is on a second HD all by itself (K drive named Storage)

I use colorfull names (Vista-Boy, Dicovery-XP) as neumonic device :)

Running three OS is not for the faint of heart. Vista is necesary because of work software (Auto CAD and Adobe Photoshop). XP is still there because of games :) and Linux is there because it is the future and I will transition totally when I can git my work software versions for linux :KS

---

### Post by mayagrafix on 2009-09-06
> **Nepherte said:**
> It's used as a boat loader: I suggest you keep it unless you don't want to be able to boot your computer.

OK, I thought about it and you are right. I use Windows on HD1 and have Ubuntu on HD2 so this must be were GRUB resides. It makes sence for GRUB to locate on FIRST HD. 

Now that I know what and why, I can sleep easy. THANKS!!!!:KS

---

### Post by mayagrafix on 2009-09-06
> **P4man said:**
> what does the readme say ? :)

Im guessing its a left over from an attempt to make a bootable stick or something?
[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/DirectorioSyslinux02.jpg[/IMG]

As u can see above I looked for readme but found none, txt docs have other data non regarding install or version.

I think Nepherte nailed it when he ID this directory as bootloader which makes sense because I have multiple OS installed in this box (Vista, XP and Ubuntu)and this is on main disk at first level (C:\syslinux)

I also thought it was a leftover from Ubuntu LiveCD instalation, although you might have point about bootable USB drive because one time I tried to make a DSM (Damm Small Linux) install... so I'll research this idea a bit more. 

I will rename directory and see what happens. If GRUB related then I will boot directly into Windows Vista and if not we can guess it is leftovwer from DSM install.

Thanks to all for great help, have a nice day!

---

### Post by mayagrafix on 2009-09-07
UPDATE: I changed the directory's name and re boot  and nothing happens. So best idea is leftover from DSM install.

Thanks to all for interest and helpful ideas to this problem :KS

---

