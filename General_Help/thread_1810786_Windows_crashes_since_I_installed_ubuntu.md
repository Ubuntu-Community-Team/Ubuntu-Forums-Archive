---
title: "Windows crashes since I installed ubuntu"
date: 2011-07-23
forum: General Help
---

### Post by Mezgrman on 2011-07-23
Hello community,

first I want to say that I was a windows user just about a week ago. Then I installed ubuntu on a USB flash drive, just for fun, and now it's installed as main OS on my laptop and the only thing I use windows for is syncing my iPod touch with iTunes. (Yes, I know about other possibilities to copy music to it from ubuntu, but I want to continue using iTunes.)

Now my main problem is that since I installed ubuntu (10.10 Maverick Meerkat), my windows (Windows 7 Home Premium 32 Bit) sometimes crashes during startup. Sometimes it boots up perfectly normal, then in some cases it crashes at the first attempt to boot and when I retry and choose "Start Windows normally" it works just fine and then there are the times when it crashes everytime I try to boot. I wasn't able to find out why it sometimes works and sometimes doesn't. I also removed all USB devices during startup but that didn't change it.
I noticed that when I start Windows in safe mode first, it works, then I restart and choose normal mode and it works too.

So, my question is: Has anybody experienced this issue and/or knows a way to fix it? It's just annoying to have to try several times just to be able to keep my iPod synced.

Greetings,
Julian aka Mezgrman. :)

---

### Post by TeoBigusGeekus on 2011-07-23
If you used the ubuntu installer to partition your drives, it could be this: win7 doesn't like much fiddling with its partitions - you should have used its own disk management tool to create new partitions.

As for keeping windows just for using itunes, may I suggest a virtual machine?

---

### Post by Mezgrman on 2011-07-23
> **TeoBigusGeekus said:**
> If you used the ubuntu installer to partition your drives, it could be this: win7 doesn't like much fiddling with its partitions - you should have used its own disk management tool to create new partitions.

As for keeping windows just for using itunes, may I suggest a virtual machine?
Well, I had 15 GB of free disk space on my hard drive and used it to install ubuntu (on one single partition). I didn't change anything at my windows partition. Concerning a VM, hmm, yes, maybe, but I'd like to keep my windows working anyway... you never know what it could be good for one day ;)

---

### Post by TeoBigusGeekus on 2011-07-23
> **Mezgrman said:**
> Well, I had 15 GB of free disk space on my hard drive and used it to install ubuntu (on one single partition). I didn't change anything at my windows partition. Concerning a VM, hmm, yes, maybe, but I'd like to keep my windows working anyway... you never know what it could be good for one day ;)

Agreed, but the installer created a new partition with these 15gb, didn't it?

---

### Post by Mezgrman on 2011-07-23
> **TeoBigusGeekus said:**
> Agreed, but the installer created a new partition with these 15gb, didn't it?

Yes, it sure did. But since I can't create an ext3 partition using the windows disk management tool, what else should I have done? :confused:

EDIT: With "free" I meant unpartitioned disk space, just to clarify that.

---

### Post by TeoBigusGeekus on 2011-07-23
You should have gone to Administrative tools>Disk management inside win7 and created a new empty partition (ntfs or fat, doesn't matter). Then you would format the partition with ubuntu's installer and install it there.

---

### Post by Mezgrman on 2011-07-23
> **TeoBigusGeekus said:**
> You should have gone to Administrative tools>Disk management inside win7 and created a new empty partition (ntfs or fat, doesn't matter). Then you would format the partition with ubuntu's installer and install it there.

Oh. That makes sense. So you think there's no chance I could get rid of the crashes besides reinstalling ubuntu?
If this is the case I'd prefer living with the crashes... ;)

---

### Post by TeoBigusGeekus on 2011-07-23
> **Mezgrman said:**
> Oh. That makes sense. So you think there's no chance I could get rid of the crashes besides reinstalling ubuntu?
If this is the case I'd prefer living with the crashes... ;)

If this is the case indeed, the remedy would be to reinstall windows and then reinstall grub2.
Who needs all this? :P

---

### Post by Mezgrman on 2011-07-23
> **TeoBigusGeekus said:**
> Who needs all this? :P

Not me :)

---

