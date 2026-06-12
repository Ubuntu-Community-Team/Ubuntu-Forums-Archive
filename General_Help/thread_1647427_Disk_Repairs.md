---
title: "Disk Repairs"
date: 2010-12-17
forum: General Help
---

### Post by Spyderkid on 2010-12-17
I booted up ubuntu and at the load up screen it said "attempting disk repairs this may take a while" or something very similar to this. Is that normal? is it just do a routine thing? because nothing was wrong with it when I shut down before

---

### Post by QLee on 2010-12-17
> **Spyderkid said:**
> I booted up ubuntu and at the load up screen it said "attempting disk repairs this may take a while" or something very similar to this. Is that normal? is it just do a routine thing? because nothing was wrong with it when I shut down before

This might be one of the times that the exact message would make things clearer.

Your system will do a disk check on the root partition after a set number of boots, to make sure it is clean.

If there was an unclean shut down of a partition, that would also trigger a filesystem check.

If you want to verify all the partitions on your system, you can boot with the live CD and check the unmounted (they should be unmounted for checking, although mounted read only might be OK) partitions from there with gparted or from the command line with, fsck.

Did your system find any errors or did it take a really long time?

---

### Post by Spyderkid on 2011-01-04
It was very quick under a minute easily no errors.

---

### Post by Rubi1200 on 2011-01-04
By default, Ubuntu checks the file-system for errors/integrity every 30 boots.

You probably saw something like this:
[http://ttcshelbyville.files.wordpress.com/2010/12/forcefsck-checking.jpg](http://ttcshelbyville.files.wordpress.com/2010/12/forcefsck-checking.jpg)

If there were problems, you probably would have noticed. The time-frame sounds about right, so I would not be too concerned about it.

---

### Post by nomko on 2011-01-04
> **Spyderkid said:**
> I booted up ubuntu and at the load up screen it said "attempting disk repairs this may take a while" or something very similar to this. Is that normal? is it just do a routine thing? because nothing was wrong with it when I shut down before
 
It is normal since after every 30 times booting, Ubuntu checks the integrity of all disks. You can set the interval manually using the terminal.
 
- open a terminal
- type in: [COLOR=#0000ff][COLOR=black]**sudo tune2fs -c ### /dev/*****[/COLOR][/COLOR]

[COLOR=#0000ff][COLOR=#000000]Where:[/COLOR][/COLOR]
[COLOR=#0000ff][COLOR=#000000]### = number (which stands for the number of interval)[/COLOR][/COLOR]
[COLOR=#0000ff][COLOR=#000000]*** = partition (of which the interval has to be changed)[/COLOR][/COLOR]

[COLOR=#0000ff][COLOR=#000000]As example:[/COLOR][/COLOR]
[COLOR=#0000ff][COLOR=#000000][COLOR=#0000ff][COLOR=black]sudo tune2fs -c 1000 /dev/sda1[/COLOR][/COLOR][/COLOR][/COLOR]
[COLOR=#0000ff][COLOR=#0000ff][COLOR=#000000]After 1000 times booting, partition sda1 will be checked for integrity[/COLOR][/COLOR][/COLOR]

---

### Post by Spyderkid on 2011-01-05
Thanks rubi1200 I did see something almost identicle to what you posted on the hyper-link

excuse spelling on identicle

---

### Post by nomko on 2011-01-05
> **Spyderkid said:**
> Thanks rubi1200 I did see something almost identicle to what you posted on the hyper-link

excuse spelling on identicle

Did you perform the command i gave you??
With that you can set the interval much higher.

---

### Post by Spyderkid on 2011-01-06
I don't need to change it for now but thanks for the command for future refrence

---

