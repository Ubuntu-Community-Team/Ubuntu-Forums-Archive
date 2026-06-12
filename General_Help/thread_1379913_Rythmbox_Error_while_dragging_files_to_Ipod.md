---
title: "Rythmbox: Error while dragging files to Ipod"
date: 2010-01-13
forum: General Help
---

### Post by Wandels on 2010-01-13
[http://img211.imageshack.us/img211/9098/ipodd.png](http://img211.imageshack.us/img211/9098/ipodd.png)

Any know what the problem is and how I can solve it?

---

### Post by brickhead248 on 2010-01-13
> **Wandels said:**
> [http://img211.imageshack.us/img211/9098/ipodd.png](http://img211.imageshack.us/img211/9098/ipodd.png)

Any know what the problem is and how I can solve it?
hmm, it seems like the file for track 12 is set to read only for some reason, maybe another process has the file open. close some processes that may be using it (or stop playing it in rythmbox) and then check out the file's properties to see if it has been set to read only. then try again

good luck

---

### Post by brickhead248 on 2010-01-13
> **brickhead248 said:**
> hmm, it seems like the file for track 12 is set to read only for some reason, maybe another process has the file open. close some processes that may be using it (or stop playing it in rythmbox) and then check out the file's properties to see if it has been set to read only. then try again

good luck
looking at your screenshot again, it seems like there are multiple errors. it seems like a process is using all the files that make up the album. again, see if this is because another process is using it, OR maybe another instance of rythmbox is copying the files to the ipod at the same time?

if nothing works, be patient and:
1. reboot
2. open rythmbox
3. copy files over

---

### Post by Wandels on 2010-01-13
Could the error occur because all my music files are on a external hd?

---

### Post by nothingspecial on 2010-01-13
Was your ipod formatted on a mac?

---

### Post by Wandels on 2010-01-13
Yes

---

### Post by nothingspecial on 2010-01-13
Then you have a problem. A mac will format your ipod as hfs++. This is mounted as read only by default in linux.

The simplest way to fix this (assuming you have access) is to reformat it on a windows computer running iTunes.

It is possible to use it as it is, but that will involve a bit of terminal work and editing fstab. (Unless anyone knows an easier way).

It`s up to you, do you have (or does a friend of your`s have) a windows box running itunes?

---

### Post by Wandels on 2010-01-13
Yeah, I do have friends who run iTunes on a Windows machine but then I have to go over there. :D
I read somewhere that you could run iTunes on Ubuntu with some tweaks. Hard to do so?


Thanks for your time man!

Edit: isn't Wine an option? to format iPod on a windows machine.

---

### Post by nothingspecial on 2010-01-13
> **Wandels said:**
> Yeah, I do have friends who run iTunes on a Windows machine but then I have to go over there. :D

I`d suggest doing that then.

> **Wandels said:**
> I read somewhere that you could run iTunes on Ubuntu with some tweaks. Hard to do so?

Never tried it. Once you reformat your ipod, rhythmbox will work just fine.

> **Wandels said:**
> Thanks for your time man!

No problem :D

---

### Post by nothingspecial on 2010-01-13
Reply to edit....

I don`t know how well it will work.

---

### Post by Wandels on 2010-01-13
Okay, tryed installing iTunes via Wine but can't seem to find the launch file :(. Quicktime is installed though.

It'll be awhile till I get access to a Windows machine so any other suggestions are welcome!

---

### Post by docus on 2010-01-13
Hopefully someone will correct me if I'm wrong, but I don't think iTunes runs properly in Wine?  You could try installing XP in a virtualbox and running iTunes from there.

(I haven't tried either myself)

---

### Post by nothingspecial on 2010-01-13
Do you have a Mac then?

You need to disable journaling on your ipod, but from a mac

[SIZE="2"]*_This is a Mac command_*[/SIZE]

     ```
diskutil disableJournal /Volumes/iPod
```

---

### Post by blur xc on 2010-01-13
> **docus said:**
> Hopefully someone will correct me if I'm wrong, but I don't think iTunes runs properly in Wine?  You could try installing XP in a virtualbox and running iTunes from there.

(I haven't tried either myself)


I run itunes from windows in vbox, works just fine...

BM

---

### Post by Wandels on 2010-01-14
> **nothingspecial said:**
> Do you have a Mac then?

You need to disable journaling on your ipod, but from a mac

[SIZE=2]*_This is a Mac command_*[/SIZE]

     ```
diskutil disableJournal /Volumes/iPod
```

I'll try this when I get home. Thanks!

---

### Post by Wandels on 2010-01-14
```
Macintosh-5:~ benwandels$ diskutil disableJournal /Volumes/iPod van Ben
Disk Utility Tool
Usage:  diskutil enableJournal MountPoint|DiskIdentifier|DeviceNode
        diskutil disableJournal [force] MountPoint|DiskIdentifier|DeviceNode
Enable or disable journaling on an HFS Extended volume.  The volume will be
temporarily mounted if necessary, so normally this works whether or not the
volume is mounted.  The force option, however, causes a direct write to the
on-disk volume data, and requires that the volume not be mounted.
Ownership of the affected disk is required.
Example: diskutil enableJournal /

```

So is it disabled now or what? :???:

---

### Post by Wandels on 2010-01-16
Sorry but... BUMP

---

### Post by jamesisin on 2010-01-16
I think you want to replace /Volume/iPod with the actual path to your iPod.  If your iPod name contains spaces (is that possible?) you will want to put that path in quotes.

---

