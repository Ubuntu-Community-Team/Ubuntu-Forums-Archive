---
title: "Unsatisfactory characteristics of GRUB 2?"
date: 2010-09-13
forum: General Help
---

### Post by aajax on 2010-09-13
Now that I've finally learned how to use GRUB along comes GRUB 2.  From my vantage point the developers seem to have overlooked some basics.  Possibly, hopefully, I just need someone to straighten me out.  Therefore I make some observations and would be grateful for someone to point out how I'm wrong.

To begin with it seems natural that a boot loader ought not depend on being able to boot the system in order to configure the settings used for booting.  This is especially true for one calling itself grand.  As best I can tell GRUB (legacy that is) does accomplish this but I'm having my doubts about GRUB 2.  For example, I use GRUB as a boot manager whose job it is to boot other OS's on the same computer.  I want the boot manager to be out of site and out of mind (i.e., simple to update on the rare occasion when that might be needed).  Therefore, I install it in a tiny FAT/DOS partition that I always create at the beginning of any new drive.  This allows me to create multiple other partitions used to boot different OSs (e.g., in my case several versions of Linux and Windows).  This means that every partition that has an OS installed on it also has the necessary software for loading that OS.  In the case of Ubuntu this had become GRUB and now is GRUB 2.  An important point here is that I do not expect nor want any Ubuntu system to load/boot any system other than itself.  Ubuntu (GRUB 2 if you prefer) seems to go to great lengths to find other systems and configure itself to boot them.  If this were done via what GRUB calls chain-loading this wouldn't be to bad.  In that, it would fit my purpose pretty well.  However, GRUB has this characteristic, that I find quite undesirable, where it may load a kernel and/or mount a root filesystem from a different partition than the one from which GRUB was loaded.  When cloning systems it becomes very easy to ruin multiple systems (i.e., not just the one where you made a configuration error but other stable systems as well).  While some folks may like this feature I argue that there is a need for an easy foolproof way to disable it.  Better yet this should be the default and those that want additional sophistication should have to enable it intentionally.

Something that I do a lot is to clone systems.  The purpose is to try new or different things on a new system such that you don't screw up something that is working good while you experiment.  It also provides a good method of recovering form errors that you are having difficulty troubleshooting but you aren't quite ready to trash the system that is acting up.  Unfortunately you cannot count on GRUB to leave a stable system alone.  The Ubuntu technique for using UUID to identify partitions causes a very particular problem when trying to clone a system.  When a partition image is created it includes the UUID.  This means that when you restore the image file to a different partition the cloned system partition has the same UUID as the original partition.  I've been able to circumvent this problem by changing the UUID on a live system partition before restoring an image of it to another partition.  To be sure this technique risks causing a boot problem where one didn't previously exist which to my way of thinking is also poor technique.  To do this I have to be able to update the GRUB configuration before being able to boot the restored partition.  There are various ways to do this that basically involve mounting the newly restored partition and editing menu.lst (or whatever file might be appropriate).  However, what you very definitely cannot do is to depend on booting the system in order to run the update-grub script.

It seems that GRUB 2 intends that the /boot/grub/grub.cfg file should not be edited.  It provides a means to add custom menu entries by editing files in /etc/grub.d.  However, this technique also depends on being able to run update-grub which cannot be done until after you have a way to boot the system.  As best I can tell my only alternative is to edit grub.cfg.  Does anyone have a better idea?

---

### Post by drs305 on 2010-09-13
> **aajax said:**
>  While some folks may like this feature I argue that there is a need for an easy foolproof way to disable it.  Better yet this should be the default and those that want additional sophistication should have to enable it intentionally.


If I'm following what you want, you can turn off the ability of G2 to search for other OS's. You can add the following line to */etc/default/grub* or run the second mode so the script isn't executable.

/etc/default/grub:
> GRUB_DISABLE_OS_PROBER='true'

or run:
```
sudo chmod -x /etc/grub.d/30_os-prober 
```
You could even run the following, and just keep a custom menu with no automatic updates.
```
sudo chmod -x /etc/grub.d/10_linux /etc/grub.d/20_memtest86+ /etc/grub.d/30_os-prober 
```

I've got to run, so that's as far as I've gotten. I'll read through the rest later.

---

### Post by Zimmer on 2010-09-13
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

Have a look and see if there are any ideas here that may help...

From the average (I think) user perspective I have found GRUB2 to be nice and easy for a multi boot arrangement.
I have a laptop with Win and Ubuntu 8.04 in tandem and an external USB drive with 3 other Linux installs (one 10.04 and GRUB2 on its MBR).
When I installed the extra Linuxes I just ran the Grub update command and 
GRUB2 found and referenced all the installs USB and HDD.
Without the USB plugged in my old system (using EASYBCD ) takes control.
Now I have grown accustomed to GRUB2 I am considering installing it to the MBR of the Laptop drive and forgetting about EasyBCD.

---

### Post by drs305 on 2010-09-13
> **aajax said:**
> 
Something that I do a lot is to clone systems.  ...  I've been able to circumvent this problem by changing the UUID on a live system partition before restoring an image of it to another partition.  To be sure this technique risks causing a boot problem where one didn't previously exist which to my way of thinking is also poor technique.  To do this I have to be able to update the GRUB configuration before being able to boot the restored partition. 

Again in */etc/default/grub* there is a setting to turn off the UUID feature:
> #GRUB_DISABLE_LINUX_UUID="true"
Remove the # symbol for this feature to take effect. I don't know whether this turns off the UUID feature internally as the various G2 scripts run in background, or just on the menu output, but it's a place to start.

You will probably note the inconsistent use of the quotation marks. This is a carryover from when G2 was being developed. My theory is that different devs did different parts, and it appears that no standard was set for how to present the values - there were single quotes, double quotes, and no quotes. I mention this because there was a bug in this particular setting that required quotes around either "true" or "false". I don't know if that is the case any longer, so I included them.

I have written a variety of posts (see signature line) about how to alter the G2 scripts. *grub.cfg* is not supposed to be edited but it can be highly versatile by allowing the user to modify the scripts however he/she wishes. I no almost nothing about scripts, but I've managed to create some that hide particular partitions, rename titles, hide multiple listings, etc. So if I can do these basic things anyone with programming or scripting experience could probably do some pretty neat things with Grub 2.

Finally, although G2 needs files within an OS, the G2 command line/rescue options are pretty robust - if a system's files are not corrupted there is a very good probability that a knowledgeable user can use the G2 terminal to load modules, set directories and boot into the OS. 

I'm not saying that G2 doesn't have it's faults. It does. But there are a few regular posters on these forums who are heavy-duty multiple-OS kind of people. Some were originally very skeptical of G2 but have been won over by it's versatility. I think that one of G2's stronger points is it's ability to adapt to multiple-OS environments. So keep an open mind for a bit longer.

The G2-Basics and GRUB2 links in my signature line can give you the basics of how it works and the others mostly cover how to do something specific.

---

### Post by QLee on 2010-09-14
[QUOTE=aajax]...
Something that I do a lot is to clone systems.  The purpose is to try new or different things on a new system such that you don't screw up something that is working good while you experiment.  It also provides a good method of recovering form errors that you are having difficulty troubleshooting but you aren't quite ready to trash the system that is acting up.  Unfortunately you cannot count on GRUB to leave a stable system alone.  The Ubuntu technique for using UUID to identify partitions causes a very particular problem when trying to clone a system.  When a partition image is created it includes the UUID.  This means that when you restore the image file to a different partition the cloned system partition has the same UUID as the original partition.  I've been able to circumvent this problem by changing the UUID on a live system partition before restoring an image of it to another partition.  To be sure this technique risks causing a boot problem where one didn't previously exist which to my way of thinking is also poor technique.  To do this I have to be able to update the GRUB configuration before being able to boot the restored partition.  There are various ways to do this that basically involve mounting the newly restored partition and editing menu.lst (or whatever file might be appropriate).  However, what you very definitely cannot do is to depend on booting the system in order to run the update-grub script.
...[/QUOTE]
I'm only going to comment on this section because drs305 has made sufficient comment on the rest.

aajax, I'm sure you realise that most users do not do a lot of cloning so that case is not typical. I expect developers to concentrate on typical uses. 

In addition, you must be cloning by bit-for-bit copying in order to get the UUID carried over. I understand your example, I do something very similar ,as you state, to "try new or different things on a new system such that you don't screw up something that is working good while you experiment". To accomplish that though, I use a different method. I mirror my clone with rsync to the partition I want it on. Because I'm copying the system I want into the filesystem format that is already on the partition (with it's unique identifier already set), I avoid a system with matching UUIDs. Now, I don't mean to suggest you change you method, just to illustrate to you that what bugs you doesn't happen in all cases. Clearly, it isn't a big problem for someone knowledgeable like you because you easily found a workaround. Many people who are "cloning" a system for backup purposes do want a perfect image with the UUID so the image can be easily restored to a partition.

By the way, UUIDs didn't come in with GRUB2, legacy was also aware of them, I have a Debian Lenny install from 2008 where I use the UUID notation rather than device node in the menu.lst. 

For what it's worth, I hated GRUB2 when I first encountered it. That was mostly because I had to re-learn how to do things that I was very comfortable with previously.

---

### Post by aajax on 2010-09-14
> **drs305 said:**
> If I'm following what you want, you can turn off the ability of G2 to search for other OS's. You can add the following line to */etc/default/grub* or run the second mode so the script isn't executable.

/etc/default/grub:


or run:
```
sudo chmod -x /etc/grub.d/30_os-prober 
```
You could even run the following, and just keep a custom menu with no automatic updates.
```
sudo chmod -x /etc/grub.d/10_linux /etc/grub.d/20_memtest86+ /etc/grub.d/30_os-prober 
```

I've got to run, so that's as far as I've gotten. I'll read through the rest later.

Thanks for the tip!  I had surmised that either removing 30_os-prober or removing the executable attribute might have that affect.  However, using a configurable setting is more elegant.

> **Zimmer said:**
> [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

Have a look and see if there are any ideas here that may help...

From the average (I think) user perspective I have found GRUB2 to be nice and easy for a multi boot arrangement.
I have a laptop with Win and Ubuntu 8.04 in tandem and an external USB drive with 3 other Linux installs (one 10.04 and GRUB2 on its MBR).
When I installed the extra Linuxes I just ran the Grub update command and 
GRUB2 found and referenced all the installs USB and HDD.
Without the USB plugged in my old system (using EASYBCD ) takes control.
Now I have grown accustomed to GRUB2 I am considering installing it to the MBR of the Laptop drive and forgetting about EasyBCD.

I suppose another way I'm different from a lot of users is that my computers outlast the software.  I suspect that GRUB 2 will eventually become GRUB 3 and 4.  I've now done LILO, GRUB, GRUB 2 on the same computer.  Booting is pretty basic and it doesn't seem like it should need constant revision.  On the other hand, when upgrading to a new version of an OS it seems fair for the boot mechanism to change.  However, that change should be confined to the new system.  It should not affect others on the same computer.  Therefore, I don't want to be changing the MBR whenever a new system is installed.  As far as I can tell GRUB 2 and Ubuntu pretty well satisfies this criteria but legacy GRUB is better because its doesn't require a linux system or for that matter any OS.  I think this is a very desirable property for a boot loader.  I did make the leap and have one computer running with legacy GRUB on the MBR but I cannot foresee doing this with GRUB 2.

> **QLee said:**
> I'm only going to comment on this section because drs305 has made sufficient comment on the rest.

aajax, I'm sure you realise that most users do not do a lot of cloning so that case is not typical. I expect developers to concentrate on typical uses. 

In addition, you must be cloning by bit-for-bit copying in order to get the UUID carried over. I understand your example, I do something very similar ,as you state, to "try new or different things on a new system such that you don't screw up something that is working good while you experiment". To accomplish that though, I use a different method. I mirror my clone with rsync to the partition I want it on. Because I'm copying the system I want into the filesystem format that is already on the partition (with it's unique identifier already set), I avoid a system with matching UUIDs. Now, I don't mean to suggest you change you method, just to illustrate to you that what bugs you doesn't happen in all cases. Clearly, it isn't a big problem for someone knowledgeable like you because you easily found a workaround. Many people who are "cloning" a system for backup purposes do want a perfect image with the UUID so the image can be easily restored to a partition.

By the way, UUIDs didn't come in with GRUB2, legacy was also aware of them, I have a Debian Lenny install from 2008 where I use the UUID notation rather than device node in the menu.lst. 

For what it's worth, I hated GRUB2 when I first encountered it. That was mostly because I had to re-learn how to do things that I was very comfortable with previously.

Thanks for the tip!  I'll look into your method of cloning.  I must admit mine depends on imaging software that is becoming less and less reliable as more file systems enter into the picture.

---

### Post by QLee on 2010-09-14
[QUOTE=aajax]...
 On the other hand, when upgrading to a new version of an OS it seems fair for the boot mechanism to change.  However, that change should be confined to the new system.  It should not affect others on the same computer.  Therefore, I don't want to be changing the MBR whenever a new system is installed.  As far as I can tell GRUB 2 and Ubuntu pretty well satisfies this criteria but legacy GRUB is better because its doesn't require a linux system or for that matter any OS.  I think this is a very desirable property for a boot loader.  I did make the leap and have one computer running with legacy GRUB on the MBR but I cannot foresee doing this with GRUB 2.[/QUOTE]
It is possible to chainload from legacy GRUB to GRUB2 on the Ubuntu partition, at least on an ext3 partition that legacy understands. I believe it's not a recommended method but ... you can chainload+1 just like the Redmond OS. I think there is a method to do it to core.img on an ext4 partition too but I haven't tried that. If you did something like that you could leave a separate boot partition, which you don't mount in the other OSs and never touch your MBR and be able to edit menu.lst to you liking.

---

### Post by psusi on 2010-09-14
> **aajax said:**
> Booting is pretty basic and it doesn't seem like it should need constant revision.

There is your incorrect assumption.  It is far from basic.  It is actually rather complicated.  This is mainly because of how it has evolved over the years without any standards as new technology has been introduced.

> **aajax said:**
> On the other hand, when upgrading to a new version of an OS it seems fair for the boot mechanism to change.  However, that change should be confined to the new system.  It should not affect others on the same computer.  Therefore, I don't want to be changing the MBR whenever a new system is installed.  As far as I can tell GRUB 2 and Ubuntu pretty well satisfies this criteria

Yes -- just tell the installer not to install grub to the MBR, and you use your existing boot loader.  Just like Grub legacy.


> **aajax said:**
> but legacy GRUB is better because its doesn't require a linux system or for that matter any OS.  I think this is a very desirable property for a boot loader.  I did make the leap and have one computer running with legacy GRUB on the MBR but I cannot foresee doing this with GRUB 2.

Are you talking about the fact that you can boot a grub disk and from the grub shell, install grub to the hard disk?  I don't see why that is a desirable feature, which is probably why it has not been implemented in grub2.

As for the UUID trouble, there are two choices: use the ordinal partition number, or use the UUID.  Using the former causes breakage whenever you remove, merge, or split partitions, which are more common than copying one, hence, why they are now the default.  If you want to copy a partition, the whole point of a UUID is that it is unique, so you aren't supposed to duplicate it.  Simply change the UUID of the new copy and problem solved.

I have been thinking it would be nice to have an option to chain load other detected grub menus rather than cull the entries out of them and add them to the main menu.  That would make it a bit nicer if you want to have a single master grub that lets you load whatever other installs you have, but I think that most people prefer to just have one simple menu with all 2 or 3 choices right there, so it made sense to do it that way by default.

It also is possible to come up with a grub2 config file that will scan for all available installed operating systems at boot time and present them as choices, even with a graphical menu.  This could then be packaged as a sort of super grub package you can install if you want that kind of powerful master many boot loader.  You couldn't do that with grub legacy ;)

---

### Post by aajax on 2010-09-17
> **QLee said:**
> It is possible to chainload from legacy GRUB to GRUB2 on the Ubuntu partition, at least on an ext3 partition that legacy understands. I believe it's not a recommended method but ... you can chainload+1 just like the Redmond OS. I think there is a method to do it to core.img on an ext4 partition too but I haven't tried that. If you did something like that you could leave a separate boot partition, which you don't mount in the other OSs and never touch your MBR and be able to edit menu.lst to you liking.

Yes this is in fact how I have it running.  Then by using other tips provided herein the menu can be trimmed to exclude other systems.  This means I have to know about both GRUB (legacy) and GRUB 2, which may be satisfactory but remains less than ideal.  I think chainloading might be hard to mess up or eliminate since this is how it is done by the BIOS.

---

### Post by QLee on 2010-09-17
[QUOTE=aajax]...
 This means I have to know about both GRUB (legacy) and GRUB 2, which may be satisfactory but remains less than ideal.  I think chainloading might be hard to mess up or eliminate since this is how it is done by the BIOS.[/QUOTE]
On the other hand, we could try to put a positive spin on it and say, because GRUB2 is very good, even at this early stage, I have time to learn GRUB2 at my chosen speed. 
If you leave GRUB2 on your Ubuntu partition at defaults, then set the menu to timeout immediately, your chainload will go smoothly, even through a kernel upgrade.


Edit: I think that you may come to see good things about GRUB2 as you become more comfortable with it. It could still operate much like you do now. That separate boot partition which isn't mounted in any of your other OS after boot time gives you sufficient control over when it is updated so that you have the use of the OS prober for discovery and then you can edit the files you aren't supposed to edit to your hearts content and they won't be overwritten until you choose to do it.

---

### Post by aajax on 2010-09-17
> **psusi said:**
> 
Are you talking about the fact that you can boot a grub disk and from the grub shell, install grub to the hard disk?


I have found the Super GRUB Disk to be useful but I'm referring to the fact that GRUB legacy can be installed and maintained on a FAT partition.  I think this is attributable to the notion of having a Stage 1.5 that matches the filesystem and that booting is basic enough that the boot loader need not depend on an OS to do its' thing.  By only requiring the ability to edit a text file, GRUB legacy is more flexible than GRUB 2 which requires your Linux OS to work sufficiently well to run the update-grub script.  The fact that you have to be able to boot your system to be able to manage the booting process introduces undesirable risks that were previously unnecessary.

Possibly Super GRUB 2 Disk is the necessary alternative.

---

### Post by psusi on 2010-09-17
> **aajax said:**
> I have found the Super GRUB Disk to be useful but I'm referring to the fact that GRUB legacy can be installed and maintained on a FAT partition.  I think this is attributable to the notion of having a Stage 1.5 that matches the filesystem and that booting is basic enough that the boot loader need not depend on an OS to do its' thing.  By only requiring the ability to edit a text file, GRUB legacy is more flexible than GRUB 2 which requires your Linux OS to work sufficiently well to run the update-grub script.  The fact that you have to be able to boot your system to be able to manage the booting process introduces undesirable risks that were previously unnecessary.

Possibly Super GRUB 2 Disk is the necessary alternative.

I still don't understand... grub2 can be installed on a fat partition just fine.  You don't have to boot your system to manage the booting process, you can interact with grub2 at boot time and give it whatever commands you desire, just like grub legacy.

FYI, what grub legacy called stage 1.5 is the default condition in grub2.  Specifically the core image is written to the embed area where grub legacy's 1.5 was, only grub2's core is smart enough to allow some basic emergency command shell if it can't find the other modules on the /boot fs.

---

### Post by psusi on 2010-09-17
Oh, I see now; you're complaining about update-grub.  Of course you can edit grub.cfg by hand like you really want, but with grub2, you don't have to since update-grub figures everything out automatically.

---

### Post by dcstar on 2010-09-18
> **aajax said:**
> 
.........
The Ubuntu technique for using UUID to identify partitions causes a very particular problem when trying to clone a system.  When a partition image is created it includes the UUID.  **This means that when you restore the image file to a different partition the cloned system partition has the same UUID as the original partition.**  I've been able to circumvent this problem by changing the UUID on a live system partition before restoring an image of it to another partition.
.........

Big deal, changing UUIDs in EXT partitions is trivial, and it isn't that difficult to do in NTFS partitions any more.

The whole idea of UUIDs is to identify a partition in a manner that does not depend on arbitrary hardware designations and the advantages of that far outweigh any tiny inconveniences in having multiple copies of the partition image on a system.

---

