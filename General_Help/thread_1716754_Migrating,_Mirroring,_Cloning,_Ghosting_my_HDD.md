---
title: "Migrating, Mirroring, Cloning, Ghosting my HDD"
date: 2011-03-28
forum: General Help
---

### Post by ericjakob on 2011-03-28
Migrating, Mirroring, Cloning, Ghosting my HDD?  I'm not sure which terms are redundant or even which one I need.  I am very new to Linux and for the time being am strictly GUI oriented.

I bought a new PC with windows XP and I dont want XP.  I want it to look just like my old system with Ubuntu and all of the settings and network settings that a friend did up for me.  (I dont want to ask him to do it again.)

So I have hooked my old hd up to the secondary hd connector in my new pc.  Trouble is I can only boot into XP and I have to manoever from here.  What do I do?

I thought about going to accessories/system tools/network and settings wizzard but it seems that is only going from windows to windows and I dont think it will do what I am looking for.  

I read up on Clonezilla and it is over my head.  Besides not sure I can do it from windows.  

Basically I just want to use windows to erase itself and implement the ubuntu on the other drive with all of its settings.  

Can anyone help in laymans terms?

Oh.  one more thing.  The current system has is dual boot with XP and Linux Mint but I cant get into mint because the previous owner has it password protected.

---

### Post by seawolf167 on 2011-03-29
> **ericjakob said:**
> I read up on Clonezilla and it is over my head.  Besides not sure I can do it from windows. 

Clonezilla is super easy to use - don't be afraid! It is OS independant in that it is bootable itself and doesn't run from within Windows, Ubuntu, Mac, etc.

Steps:

[LIST]
[*]Burn yourself a Clonezilla live cd after you download it from their [website]("http://www.clonezilla.org").
[*]Insert into the cd/dvd drive of the computer you want to clone
[*]Boot off the disk (look for something like "Press F12 for boot menu", or simply change the boot order in BIOS [i.e. hit F2, del, or F8 to enter bios, then change your boot order])
[*]Select the option to "Enter Clonzeilla"
[*]Follow the instructions to "Save Image of Disk", then simply save it to your external hard drive
[*]Repeat instructions, but instead put the disk in the computer you want to have the cloned image (i.e. your new computer), then select "Restore Image to Disk" to overwrite everything on the new disk
[/LIST]
Their website very good [how-tos]("http://clonezilla.org/clonezilla-live-doc.php")for everything Clonezilla

---

### Post by Rubi1200 on 2011-03-29
Hi and welcome to the forums ericjakob :-)

A big +1 for Clonezilla. I think you will find it fulfills your needs in this area.

---

### Post by ericjakob on 2011-03-30
Thanks for the instructions.  A couple follow up questions.......  do I have to use a bootable cd or can I use a memory stick of say 16 gb?  The other question is do I need to save to an external hd or can I hook up the hd I want to clone in the slave of the new pc?  If not, then does the external hd need to have atleast as much free space as the hd I am trying to clone?

---

### Post by andrewthomas on 2011-03-31
> **ericjakob said:**
>  can I hook up the hd I want to clone in the slave of the new pc?
Yes.

> **ericjakob said:**
> 
 If not, then does the external hd need to have atleast as much free space as the hd I am trying to clone?The target drive does have to have at least as much room as the source.

---

### Post by cain071546 on 2011-03-31
is it just me or does Ghosting a HDD from a Diffrent PC onto a new hard drive for a new PC sound like it WONT WORK
you have to clean install a OS onto a newer computer

like if i copied my hard drive onto a new drive for a diffrent pc it probably wouldn't boot without a TON of errors 

just asking

---

### Post by andrewthomas on 2011-03-31
> **cain071546 said:**
> is it just me or does Ghosting a HDD from a Diffrent PC onto a new hard drive for a new PC sound like it WONT WORK
you have to clean install a OS onto a newer computer

like if i copied my hard drive onto a new drive for a diffrent pc it probably wouldn't boot without a TON of errors 

just asking
Not necessarily true.  

As a test, I put a back-up drive from an system with a phenom processor and AMD chipset into a machine with an athlon processor and a Nvidia chipset and it worked just fine.  

The only thing that I had to do was recompile my kernel in a chroot, since I only had custom kernels on the HD.

If I had a generic kernel on the HD, it probably would have booted right up.

---

