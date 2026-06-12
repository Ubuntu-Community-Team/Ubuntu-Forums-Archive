---
title: "system restore"
date: 2011-03-06
forum: General Help
---

### Post by vivek.pandey on 2011-03-06
hi every one
   is there any utility in ubuntu which is same as system restore in windows... say i messed with kernel without having a back up or something... or some other similar issue . in windows it can be restored and problems generally are solved.. so was thinking something similar here  
   thanx to all in advance :-)

---

### Post by ximhot on 2011-03-06
My laptops are getting problem with the new kernel and all died. I am looking for a similar solution too.

---

### Post by Frogs Hair on 2011-03-06
There is nothing like system restore in Ubuntu but there are backup options . Some users keep an old kernel so they have the option boot from and use the old kernel if there is a problem with the new one.  Check Remastersys for creating a backup or live cd of your current os configuration. [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by vivek.pandey on 2011-03-06
> **Frogs Hair said:**
> There is nothing like system restore in Ubuntu but there are backup options . Some users keep an old kernel so they have the option boot from and use the old kernel if there is a problem with the new one.  Check Remastersys for creating a backup or live cd of your current os configuration. [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

is it not possible for ubuntu developers to write patch that can be compiled with the kernel and a utility like system restore comes in ubuntu too , after all every one knows how useful is system restore ?

---

### Post by tordeu on 2011-03-06
If you haven't already, you could check out backup solutions like SBackup, Back in Time, Flyback, TimeVault etc. They are general backup solutions and can be used to backup pretty much the complete system.
Another alternative is to use rsync to keep a complete system clone on a separate hard drive, so in case you mess something up, use can pretty much just boot your old system from the backup drive without having to restore anything (or you could just restore your system from that drive).  
I hope that something like that is useful for your needs.

---

### Post by grahammechanical on 2011-03-06
> after all every one knows how useful is system restore ?

I do not! And I do not require a system restore because Canonical allows me to have Ubuntu install discs. And I get regular updates and upgrades. And as someone has already said, if I hit a problem with one kernel, I simply choose the last kernel that I was using.

I do not doubt that a system restore function is necessary for someone using Microsoft Windows because of all the crashes and virus infections. Do not forget that you need a place to store your system restore points. This is why you loose half you disc space.

You want the developers to spend their value time and skills creating something that is not needed. No thanks. I am happy that they continue developing Linux and all the bits that make a linux distribution.

Regards.

---

### Post by vivek.pandey on 2011-03-06
> **grahammechanical said:**
> I do not! And I do not require a system restore because Canonical allows me to have Ubuntu install discs. And I get regular updates and upgrades. And as someone has already said, if I hit a problem with one kernel, I simply choose the last kernel that I was using.

I do not doubt that a system restore function is necessary for someone using Microsoft Windows because of all the crashes and virus infections. Do not forget that you need a place to store your system restore points. This is why you loose half you disc space.

You want the developers to spend their value time and skills creating something that is not needed. No thanks. I am happy that they continue developing Linux and all the bits that make a linux distribution.

Regards.

but what if all kernels get some problem or i want my syatem to go back to some particular state and i dont have a kernel for that..? what if installed a bunch of softwares and now since i have run out of space i want the last few ones to be deleted so its best i just restore to a specific state.. right?

---

### Post by papaapa on 2011-03-06
Seriously, Restore programs are unnecessary? 

I want to thank the previous post for mentioning apps i hadn't known about.

Rsync is awesome but crafting a script to use it is cumbersome. GUI's are easy and limited but not by that much for a single user.

Plug in a thumb drive start the backup and worry less about modifying anything or everything. With each change learning more about how things work and (Haha) don't work.

In time Ubuntu will have an even faster install something like the less than 10 min install promised with Win8. Even then OEM Adware and DRM on applications are certain to stretch it to an hour or an afternoon.

Linux allows the freedom to modify and explore while learning how computers really work. Priceless.

---

### Post by MARP1961 on 2011-03-06
If you organise a future installation of Ubuntu, consider a manual partitioning and choose to have a separate root (/) and Home (/Home) partition. Your data and settings are mostly held in the /Home partition and if you encounter problems it is so simple to just reinstall Ubuntu to the /partition, leaving your /home partition unformatted. You may have to reinstall your software but that is really easy with the Software Centre. Ubuntu doesn't need a system restore facility when reinstallation is as simple as this.

---

### Post by tordeu on 2011-03-07
Reinstallation and a separate /home partition are definitely useful, but there I think there are still situations where those are not sufficient.

One of the problems is that a lot of configuration files that will most likely get modified at some point (like fstab, hosts, exports etc.) are not on /home, so reinstalling Ubuntu will also give you clean versions of those files.
Of course, you could just back up those configuration files that you modified (which I think is a very good thing to do), but then you need to keep track of all the files you modified that's why I am always thinking is: "What if I there is a file I missed"?

The Need to do all these little configurations and tweaks all over again (sometime just to fix a problem) can cost a lot of time, especially if you fixed an error ages ago and can't remember how the fix worked).

That is why I like to have a complete backup of my system. I have an additional hard disk where I installed Ubuntu on and once a weak I rsync everything to that disk (+ I keep a copy of the original fstab or that drive), so if something should totally break my system, I can use the original fstab of that drive to make the rsynced fstab work and then I can boot from there. This way, it should only take a couple of minutes and you're good to go.
I honestly have to admit, that I have not tested that drive in some time now. But the main reason I do this kind of backup is that I have a copy of everything. So, even if the drive would not boot for some reason, I do not have to ask myself If I missed something that I should back up.

Additionally I currently use SBackup to backup most of the system the more important files (like all my development stuff), so that I have a lot of "snapshots" I could restore.

And I use bazaar for a lot of things as well, which has the advantage that even if you only clone you system once in a while and don't keep a lot of snapshots in some way, shape or form, you still have snapshots for a lot of files/folders where you want or need them (development stuff (of course), but also config files, scripts, documents, ...)

Long story short: I think system restore is great, but there already are enough tools out there to achieve pretty much everything you could want.

---

### Post by Frogs Hair on 2011-03-07
> **neo_aryan said:**
> is it not possible for ubuntu developers to write patch that can be compiled with the kernel and a utility like system restore comes in ubuntu too , after all every one knows how useful is system restore ?
 
I did not mean to rely on old kernels but use them as a means of booting until find out what went wrong with the new one. I really don't know what developers have in mind for backup or system restore . I doubt it would be anything like Windows .

---

