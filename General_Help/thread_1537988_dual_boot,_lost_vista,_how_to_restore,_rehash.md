---
title: "dual boot, lost vista, how to restore, rehash"
date: 2010-07-24
forum: General Help
---

### Post by sepdna42 on 2010-07-24
There are way too many answers from archives on this so I decided to ask it again to maybe remove the confusion, for me and others.

I had Vista and Ubuntu as dual boot, something ate my Vista doc settings folder (probably me).  I want to reinstall it.  It won't because of the set up in the grub I guess.  I am not a serious Linux command line person but do follow directions well.  Is there some somewhat easy way for me to restore my Vista?

I am aware of Win 7 etc.  I have a Dell laptop so want to use the Dell restore CD.  I am not alone in this.  I run into people all over with a similar problem.  HELP!!!

---

### Post by Mark Phelps on 2010-07-24
> **sepdna42 said:**
> I had Vista and Ubuntu as dual boot, 
Did you have Ubuntu installed via Wubi? OR did you have it installed to its own seperate Ext4 partition?  It makes a lot of difference which one you did.

>  I want to reinstall it.  It won't because of the set up in the grub I guess.  I am not a serious Linux command line person but do follow directions well.  Is there some somewhat easy way for me to restore my Vista?
Restore as in -- restore it from the original factory settings? Or, restore as in restore the files/folders that you lost?

If the first, yes; if the second, no.

> I am aware of Win 7 etc. What does Win7 have to do with (1) the problem, and (2) what you want to do to solve it?
>   I have a Dell laptop so want to use the Dell restore CD. 
Don't have a Dell, but from experience with other preinstalled machines, the vendor-provided restore CD will reset the machine back to the state it was in when you first opened the box, meaning, all files, accounts, settings, will be lost. It will most probably completely reformat your drive in the process -- removing any Ubuntu installation. 

Is this what you want to do? Because, if it works, THAT is what the restore CD will do.

I'm saying IF it works, because Dells typically come preinstalled with 4 primary partitions, and folks often DELETE the Recovery partition so they can create a new one for Ubuntu.  IF you did that, you will most probably NOT be able to restore Vista -- if all the Dell Restore CD does is boot you into WinPE and launch a restore using the (now lost) MS Windows Vista Image file stored in the (former) recovery partition.

---

### Post by narnia_fan12 on 2010-07-24
If you can access BIOS, (usually f5 or f12 on boot) you can access you windows settings. You need to find the boot priorities. There are usually instructions on the side that will tell you how to switch priorities. Switch from hard drive to CD/DVD. Now, save. Insert your recovery CD, and boot. You should access the CD no problem... if there's no BIOS, I wouldn't be sure what to do, imho.

---

