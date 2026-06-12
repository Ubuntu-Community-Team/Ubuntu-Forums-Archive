---
title: "How-to recover a lost partition"
date: 2010-11-29
forum: General Help
---

### Post by robnoyes on 2010-11-29
I need a way to recover my Windows partition that was completely repartitioned when I originally moved to Ubuntu.

When I first moved to Ubuntu 8.04, I somehow overwrote my Windows partition. It happened on a laptop and since then, I've purchased a new one so I can now go back and attempt to unzip the partition holding 10.04 and get to the files I had under Windows.

Does anyone have a solution?

Thanks in advance.

---

### Post by Yarui on 2010-11-29
If you haven't written any data over the partition since it was lost, it shouldn't be difficult to get it back.  There are a lot of different partition and data recovery tools.  I have never had to recover a partition before so I can't really recommend any specific tool to you, but it should be easy to find one.

A quick search in synaptic for "partition recovery" brings up testdisk and mondo.  Maybe read a bit about what each one does and you can decide which sounds more suited to you.

---

### Post by ghostborg on 2010-11-29
[http://ubuntu-rescue-remix.org/]("http://ubuntu-rescue-remix.org/")

I used this once with success in the past.
It always happens when you least expect it.

---

### Post by ajgreeny on 2010-11-29
If your install of Ubuntu overwrote windows, and you have since been using Ubuntu as your main OS, I do not think you are likely to get much of the original windows back, I'm afraid, as you will have been writing to what was the old windows partition using your new Ubuntu install.

You can try testdisk, but do not expect too much.

If you have not been using the Ubuntu install, there is a chance windows partition is still there unscathed, but that seems a little unlikely from your story of events.

---

### Post by Yarui on 2010-11-29
Even if he has been using Ubuntu, though, I find it unlikely it has already been writing data onto the other partition if it wasn't the first partition on the disk.... but come to think of it there is probably a pretty good chance that windows was the first partition, so that would make it a bit unlikely to be able to recover the partition.

The majority of the data, however, will likely still be intact.  If you run a data recovery program, preferably from a live cd as previously suggested, you might still be able to save all your files before repartitioning.  If you have to do that, though, be aware that you need to copy the recovered data to a different hard drive to ensure that the copy doesn't overwrite the original while copying, making it impossible to complete the process.  After the data has been recovered it is safe to copy it all back to the original drive, though.  Just be sure you have everything you need recovered before you do that.

---

### Post by karthick87 on 2010-11-29
**Try TestDisk**

```
sudo apt-get install testdisk
```

Type testdisk in terminal and scan your harddisk

```
sudo testdisk
```

[[COLOR=Red]**Also check this tutorial**[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

---

### Post by ajgreeny on 2010-11-29
> **karthick87 said:**
> **Try TestDisk**

```
sudo apt-get install testdisk
```Type testdisk in terminal and scan your harddisk

```
sudo testdisk
```[[COLOR=Red]**Also check this tutorial**[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")
No!  Don't use your hard disk any more if you can avoid doing so, but use a live CD.  The more you use ubuntu, the greater the risk of overwriting the windows files you are trying to recover.

---

