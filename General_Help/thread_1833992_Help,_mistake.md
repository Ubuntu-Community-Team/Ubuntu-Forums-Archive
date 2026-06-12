---
title: "Help, mistake"
date: 2011-08-26
forum: General Help
---

### Post by LunarSandwich on 2011-08-26
ok so

I created a partition to install some files on to keep.... then I thought hey I could put ubuntu on there too 

and now I'd like to remove the partition and create another partition purely for Linux

I don't care about the data I've backed it up

but the problem is

Wubi says 

[IMG]http://i53.tinypic.com/257mwbq.png[/IMG]

and so I can't uninstall ubuntu that way

So my question is

If I wipe or merge the drive will that remove the start up selection for ubuntu?

or do you know of a way to repair that error so I can safely uninstall it and put it all on a new drive?

---

### Post by LunarSandwich on 2011-08-26
Woo hoo

I fixed my problem sort of by removing the need to uninstall ubuntu (but I'd still like to fix that issue)

I used a software which I won't name, and I resized the partition and out of the unallocated space I moved that back to my main partition

now Linux has it's own partition woo hoo

but still need help with that wubi error, I can't just leave it be I'm too pesky for that haha

---

### Post by bcbc on 2011-08-26
If wubi won't uninstall using it's own program, then see here for manual uninstallation: [https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

---

### Post by LunarSandwich on 2011-08-26
> **bcbc said:**
> If wubi won't uninstall using it's own program, then see here for manual uninstallation: [https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

If I do this, will that install a SECOND Linux? Or what will happen?

---

### Post by bcbc on 2011-08-26
> **LunarSandwich said:**
> If I do this, will that install a SECOND Linux? Or what will happen?

Those instructions are just to manually uninstall Ubuntu installed through Wubi.

---

### Post by LunarSandwich on 2011-08-28
All went well for the most part, I successfully removed it and supposedly successfully installed it onto a logical partition I made, since I can't seem to make any Primary partitions

but anywho, when I start up the machine I don't see it in the list

it's not on the bsd thinger either...

---

### Post by bcbc on 2011-08-28
I assumed that your partition dedicated to Ubuntu would be for a direct install, not with wubi. Wubi doesn't need a separate partition.

So... are you saying you reinstalled with Wubi on to the new logical drive but it's not showing on the windows boot manager, or that you installed direct and the grub menu isn't showing when you boot?

---

### Post by LunarSandwich on 2011-08-28
> **bcbc said:**
> I assumed that your partition dedicated to Ubuntu would be for a direct install, not with wubi. Wubi doesn't need a separate partition.

So... are you saying you reinstalled with Wubi on to the new logical drive but it's not showing on the windows boot manager, or that you installed direct and the grub menu isn't showing when you boot?

I installed it via Wubi on a logical drive that I set for 20 gb and used wubi to do a 10 gb install

It said everything went successful and asked me to restart my computer, but once I go to choose which OS I still didn't have Ubuntu to choose, was still just Windows 7


Do I need to allocate more space to the drive and install 17gb+ method like I did before?

Does it matter that Linux was set to a logical partition?

---

### Post by bcbc on 2011-08-28
It doesn't matter where you install when you use Wubi (or the size). You can also install directly to a logical partition - Ubuntu has no problem booting from these. There must have been a problem setting up an entry in the windows boot manager. You can check the BCD store by running *bcdedit* from an administrator command prompt or right click on "Computer", Properties, Advanced system settings, Startup and recovery settings. Check that the timeout isn't zero, and that an entry for Ubuntu exists.

If not, you could try reinstalling - or [manually create an entry]("http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/") - but you should have to manually create it. If it's just the time to display operating systems that's set to zero, set it to 15.

---

### Post by LunarSandwich on 2011-08-29
> **bcbc said:**
> It doesn't matter where you install when you use Wubi (or the size). You can also install directly to a logical partition - Ubuntu has no problem booting from these. There must have been a problem setting up an entry in the windows boot manager. You can check the BCD store by running *bcdedit* from an administrator command prompt or right click on "Computer", Properties, Advanced system settings, Startup and recovery settings. Check that the timeout isn't zero, and that an entry for Ubuntu exists.

If not, you could try reinstalling - or [manually create an entry]("http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/") - but you should have to manually create it. If it's just the time to display operating systems that's set to zero, set it to 15.

I did all of that, and it said it all worked out

it didn't

Then I just tried installing it straight through nothing customized at all, it supposedly worked (I used the disc) but it too didn't work, but under the partition names and crap I did see a Linux Swap and such so it did something, I the easybsd or w/e said it wasn't in their either....

So now I just reformatted my entire hard drive back to the factory install, after I get all my programs back I'm gonna try and get Ubuntu back on there... If it can sit in the C: partition with my Windows OS I might just have to leave it there... so much frustration lol

---

