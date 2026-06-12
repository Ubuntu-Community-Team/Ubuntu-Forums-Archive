---
title: "change fstab uuid to /dev/sdb"
date: 2010-11-13
forum: General Help
---

### Post by The standard username on 2010-11-13
Sorry for the noobish questions.   but I tried to search and couldn't find clear information. and I don't want to ruin my installation

is it safe to change fstab UUID entry for the system to /dev/sdb4  ?  
and after editing fstab, is there a script or command I need to run to release lock or update mount information?

edit:

I see not correct, and therefore not safe,but is there a format to tell linux to use /dev/sda1 instead of UUID= or label=  .

thanks again

my hard disk information can be found on this thread:
[http://ubuntuforums.org/showthread.php?t=1619509](http://ubuntuforums.org/showthread.php?t=1619509)

---

### Post by jocko on 2010-11-13
Your fstab currently has an entry with a UUID and you want to change it to /dev/sdb?
In that case, **bad idea**. The device nodes will often change between boots, so you will end up with a system that sometimes fails to mount your partition.

---

### Post by The standard username on 2010-11-13
> **jocko said:**
> Your fstab currently has an entry with a UUID and you want to change it to /dev/sdb?
In that case, **bad idea**. The device nodes will often change between boots, so you will end up with a system that sometimes fails to mount your partition.

why would it change if it has the same controller connection?  I maybe wrong . but I thought sda and sdb sequences connected to the sata controller connection, if I switch for example the hard disks'  sata controllers it would change, 

 However I understand UUID is a good idea. but I meant to ask for temporarily change .  i needed to change UUID of one linux hard disk installation, I got permission denied.  I realized later the permission problem caused by me forgetting to add sudo before each command.    but not sure if it had worked if the fstab contained the UUID that I was trying to change. hence i left my post.  my question is it possible to change it to /dev/sdb4 temporarily, and what should I add before .   because when I changed it I had an error after booting.  /dev/disk/by-uuid//dev/sdb4/  not found.  I was able to boot later as I have another linux.

---

### Post by coffeecat on 2010-11-13
> **jocko said:**
> The device nodes will often change between boots, so you will end up with a system that sometimes fails to mount your partition.

Spontaneously? Without changing the motherboard connectors around? Without changing the BIOS settings?

> **The standard username said:**
> However I understand UUID is a good idea. but I meant to ask for temporarily change .

So long as you are aware of the potential issues, I don't see a problem with using /dev/sdb4 entries in /etc/fstab. I use device node references in my Gentoo fstab and I haven't rendered Gentoo unbootable - yet. :p If, by chance, the tooth fairy did pop in one night and mess with your BIOS settings, :wink: you could always boot up with a live CD and edit fstab to get your system booting again. 

Another option is to use partition labels. Make sure they are unique and 'LABEL=*label*' works as well as 'UUID=*uuid*'.

And, yes, you do have to use sudo to change the UUID of a partition. The form is:

```
sudo tune2fs /dev/sdb4 -U <uuid>
```...changing 'sdb4' and <uuid> as appropriate.

---

### Post by The standard username on 2010-11-13
> **coffeecat said:**
> ..

So long as you are aware of the potential issues, I don't see a problem with using /dev/sdb4 entries in /etc/fstab. ...

And, yes, you do have to use sudo to change the UUID of a partition.


great, but can I just add it as /dev/sdb4  /  ..etc  or is there something else. because when booted after that I got error  that it could find  /dev/disk/by-uuid//dev/sdb4      

but I'm not exactly sure that error was cause by merely that change ,it is possible it was in combination with the UUID mix up and other issues.  


yes, I did notice I have to use sudo, I just used a long command  that generate uuid and add it to the hard disk all in one line. but I'm not used to linux , and I always forget to add sudo to every command that need sudo in one line.  (;

thanks

---

### Post by coffeecat on 2010-11-13
> **The standard username said:**
> great, but can I just add it as /dev/sdb4  /  ..etc  or is there something else. because when booted after that I got error  that it could find  /dev/disk/by-uuid//dev/sdb4 

'/dev/disk/by-uuid//dev/sdb4' is wrong - there's an extra forward slash before 'dev'. It's possible there was a typo in your etc/fstab. Perhaps you had '//dev/sdb4'.

---

### Post by jocko on 2010-11-13
> **coffeecat said:**
> Spontaneously? Without changing the motherboard connectors around? Without changing the BIOS settings?
Yes. Spontaneously. The first hard drive in the boot sequence becomes /dev/sda, but all other hard drives (and usb drives) after that are just assigned in the order they are detected, which differs between boots, at least on some hardware.

But if you only have two hard drives, and never boot with a (non-bootable) usb drive connected there shouldn't be any problem...

---

### Post by The standard username on 2010-11-13
> **coffeecat said:**
> '/dev/disk/by-uuid//dev/sdb4' is wrong - there's an extra forward slash before 'dev'. It's possible there was a typo in your etc/fstab. Perhaps you had '//dev/sdb4'.

ah, I see.  maybe that what happened then.   thanks for confirming , as I didn't think it might be a typo .  I should have thought of double checking that.


thanks everyone.

---

### Post by coffeecat on 2010-11-13
> **jocko said:**
> Yes. Spontaneously. The first hard drive in the boot sequence becomes /dev/sda, but all other hard drives (and usb drives) after that are just assigned in the order they are detected, which differs between boots, at least on some hardware.

I'm glad it's only some hardware. One of my machines has 6 SATA headers and for a time I had three HDs plugged into connectors 1,2 and 3, with the drives set in that priority in the BIOS and drives 1,2, and 3 came out as sda, sdb and sdc. So far, so good.

But then I removed 'sdb' and 'sdc' replacing them with one bigger drive plugged into connector 2. The original drive 1 (with grub in the mbr) was still plugged into connector 1. At first the system wouldn't boot (I had already edited fstab from the live CD) and I found that the BIOS had taken upon itself to set the new drive 2 as drive 1.

All very odd. A bit different from what you describe, but worth being forewarned about.

---

### Post by psusi on 2010-11-13
> **jocko said:**
> Yes. Spontaneously. The first hard drive in the boot sequence becomes /dev/sda, but all other hard drives (and usb drives) after that are just assigned in the order they are detected, which differs between boots, at least on some hardware.

But if you only have two hard drives, and never boot with a (non-bootable) usb drive connected there shouldn't be any problem...

There is nothing special about sda, it is assigned on a first come first serve basis as well.  The system has no idea which drive the bios booted from.  Often times people find that if they boot with a usb flash drive plugged in, it can be assigned sda and their (booting) hard drive becomes sdb or sdc.

---

### Post by jocko on 2010-11-13
> **psusi said:**
> There is nothing special about sda, it is assigned on a first come first serve basis as well.  The system has no idea which drive the bios booted from.  Often times people find that if they boot with a usb flash drive plugged in, it can be assigned sda and their (booting) hard drive becomes sdb or sdc.
Ok. That makes using device nodes instead of uuids an even worse idea than if it worked as I thought it did...
But of course the op can try it out and see what happens. If he's lucky he won't see any problems, if he's unlucky he will end up with a system that fails to boot 50% of the time...

---

### Post by The standard username on 2010-11-13
> **jocko said:**
> Ok. That makes using device nodes instead of uuids an even worse idea than if it worked as I thought it did...
But of course the op can try it out and see what happens. If he's lucky he won't see any problems, if he's unlucky he will end up with a system that fails to boot 50% of the time...


Please see my previous posts.  I only wanted to do that temporarily. though I didn't know about the frequent changes. in fact I didn't notice that on my system.  but I might change my motherboard, or change hard disks to one bigger. so I did understand UUID is better.  I only wanted to switch fstab because I thought it was not letting me changing UUID of one hard disk.  

 I have 2 hdds, and one was backup of the other, so they had duplicate UUIDs.  So, it is not always so great. but much better than the old way (;

I already switched it back to UUID, after successfully changing UUID of one of the linux installations partition.   UUID duplication caused so much problems on my system. 


Maybe linux should adopt a newer style  for example UUID/sdaX  the sda value only get taken when there is duplication.

---

