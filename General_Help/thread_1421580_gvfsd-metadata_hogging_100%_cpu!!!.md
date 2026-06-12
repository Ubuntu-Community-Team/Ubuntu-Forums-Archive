---
title: "gvfsd-metadata hogging 100% cpu!!!"
date: 2010-03-04
forum: General Help
---

### Post by vjkeito on 2010-03-04
My system has been running fine for quite some time and then more recently it has become sluggish.  Nautilus hangs very regularly, and often required a

```
pkill nautilus
```

to get things running again.

The issue didn't appear to be getting any better so I took a look at the processes running and realized that gvfsd-metadata is hogging 100% cpu cycles and nearly 60% of memory.

I'm on a revo r3600 ION single cpu machine with 1gb RAM.  Ubuntu 32bit Karmic.

I've done some searches and seen a couple of others who appear to be suffering too ( [http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg386162.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg386162.html) ).

with this only recently becoming an issue I'm sure either an update caused the issue or there is a conflict that remains unresolved.

Please help me fix this as it is really becoming quite a bothersome problem having to issue

```
pkill gvfsd-metadata
```

at regular intervals just to carry out normal everyday tasks.


If no-one can come up with anything then I shall reformat to see if that helps and if not I'll be throwing the machine out of the window. ;)

---

### Post by vjkeito on 2010-03-04
Apparently (after having done lots of searching in the darkest depths of the internet) I have stumbled on a possible solution.

After a brief test it appears to have worked, though I haven't had time to thoroughly work the machine and make sure it is indeed running on top form.  I shall update the post as necessary in the coming days after giving it a more comprehensive workout.

**THE FIX**:

> It looks like your metadata store is got corrupted, leading to an infinite loop in the code.

FIX:
The fix here is to remove the metadata storage, located in: ~/.local/share/gvfs-metadata.

I now believe that this could well have come about after the machine completely ran out of disk space one night whilst downloading.  It seems to fall into place with regards to time-frame.

*Fingers-crossed.*

---

### Post by vjkeito on 2010-03-05
I can happily confirm that the above fix does indeed rectify this issue.  Hopefully this will at some point help others who come across this problem get their system running tip-top again.

The code to issue the fix is as follows:

```
rm -rf ~/.local/share/gvfs-metadata
```

---

### Post by diegorodriguezv on 2010-03-20
Yes, exactly the same scenario and your solution helped a lot.

Don't forget to check your hard disk space using ```
df -h
``` and free some if necessary.

Thanks.

---

### Post by Quift on 2010-04-05
Same problem for me, hopefully this will fix it.

also, might this be the same bug that leads firefox, banshee and gnome-do to crash?

will see now if they stop.

---

### Post by kflorence on 2010-04-20
Thanks vjkeito, had this problem today and this fixed it like a charm.  I think my corruption had something to do with Eclipse, since that seems to be what triggered it.

---

### Post by feralert on 2010-07-27
Great stuff vjkeito!!

Helped me a lot with your posts, so thank you very mucho.

A couple of days ago my home partition got full up and I had to remove some stuff but even so and since then gvfsd-metadata was eating resources like crazy. So following your instructions i did:

> rm -rf ~/.local/share/gvfs-metadata
pkill gvfsd-metadata

And everything went back to normal!

Cheers!!

---

### Post by dudeeh on 2010-09-25
Same problem here, most likely because my disk was also entirely full a while ago. Ever since then from time to time nautilus would become very slow and this program used like 100% cpu.

A quick google led me straight to this post and I ran the fix. It will be a while before I can actually say for sure that it is fixed, but I got a good feeling bout it :)

Thanks!

---

### Post by axeman on 2010-11-02
Thanks a lot vjkeito, this issue was driving me crazy, now my computer works great again.

---

### Post by alecz20 on 2011-02-24
I ran into the same issue a few times lately.

I had over 160 GB of free space, so I don't think that was an issue.
However, I was attempting to move about 50,000 text files from an external disk to a folder on the internal disk.

When trying to do this... nautilus became sluggish, and I was unable to open any more folders.

However, other programs ran fine (4 core CPU).

Your solution seemed to fix the problem at least temporarily.

---

### Post by achron on 2011-03-12
> **alecz20 said:**
> I ran into the same issue a few times lately.

I had over 160 GB of free space, so I don't think that was an issue.
However, I was attempting to move about 50,000 text files from an external disk to a folder on the internal disk.

When trying to do this... nautilus became sluggish, and I was unable to open any more folders.

However, other programs ran fine (4 core CPU).

Your solution seemed to fix the problem at least temporarily.

Indeed, file space seems NOT to be the issue, I had > 380 Gigs free, but was attempting to move 90,000+ files.

Nice fix, worked like a charm.

---

### Post by bc9 on 2011-04-09
I had a similar problem per my post here: 

[http://ubuntuforums.org/showthread.php?p=10658684#post10658684](http://ubuntuforums.org/showthread.php?p=10658684#post10658684)

...and this fix seems to work. Thanks!

---

### Post by d3v1150m471c on 2011-04-09
it's good practice to not fill more than 85% of your harddrive. external harddrives are cheap.

---

### Post by Fenris_rising on 2011-08-15
Well done that man!

This issue only became an issue in the past couple of days for me. Just out of curiosity I googled the gvfsd-metadata which I could see in 'top' and here I am!

As with several of you here I to was moving large quantities of data. In my case 9,525 images I was rescuing from a slide show DVD for a friend which I then had to go through to select 1 in 22 frames to get 418 single photos.

All this was dragging along because of the same issue. Fix applied and things are running at maximum efficiency as usual. I love Linux! possibly only second to this forum :biggrin:

regards

Fenris

---

### Post by Ruaridh on 2012-01-29
I've just stumbled on this problem too. (O/S upgraded to 11.11, not clean install)

My issues started when moving large numbers of files (20,000 xml files), 30 Gig partition, 70% free.

The gvfsd-metadata process ran for adout 30 minutes ... but it ***did* **finish.

I'm a bit wary of killing off a process when it is running, just in case it does bad things to my filing system.  I don't want to do anything that will cause even bigger problems later.

Has anyone had any knock on problems after using this?
```
rm -rf ~/.local/share/gvfs-metadata
```Can anyone tell me what gvfsd-metadata  does?

[edit]
Are there similar problems using scripts to move files or is it just a graphical interface thing?
[/edit]

R.

---

### Post by JRV on 2012-01-29
I had this problem a while back, over a year ago.

```
rm -rf /home/jack/.local/share/gvfs-metadata
pkill gvfsd-metadata 
```

Solved the problem and it has not happened again.  
And it does not seem to have caused any further problems.

---

### Post by anand_30 on 2012-05-04
> **vjkeito said:**
> I can happily confirm that the above fix does indeed rectify this issue.  Hopefully this will at some point help others who come across this problem get their system running tip-top again.

The code to issue the fix is as follows:

```
rm -rf ~/.local/share/gvfs-metadata
```

Thank you vjkeito,this worked.

Just installed 12.04 and had this problem of gvfs-metadata consuming all the CPU.I don't know the root of the problem but it might be because I installed 12.04 over 10.04(caelinux2011) and kept the '/home' same and in the process I had to delete many previous config folders in /home like '.gnome2' , '.wine' .
Now everything is working even smoother than a bearing:lolflag:

Thanks again.

---

### Post by spaceshipguy on 2012-09-22
Same problem. (but only 96% of CPU for me)

I was copying files to an external disk. I think the trash demon was still emptying the disk at the time.

File transfer to the disk slowed to a crawl, but the rest of the system was responsive as normal. 

I killed gvfsd-metadata with system monitor, and used your code. The progress bar suddenly accelerated in a very comical way. Thanks :-)

---

