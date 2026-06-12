---
title: "wiping hard drive clean"
date: 2010-09-23
forum: General Help
---

### Post by fidelandche on 2010-09-23
Hi all,
My laptop has had it, so I am getting a new net book instead. So with my old laptop, I am giving it to a charity who refurb them and send them overseas. Not that I do not trust them, but they say they wipe the hard drive to US Department of Defense standard 5220.22M.
 But I would feel a lot happier if I did it myself first, so how do I go about doing it? I have tried using wipe but as it was a tar file I got stuck trying to use the tar file.

---

### Post by rgiles43 on 2010-09-23
Hello,

I am not to sure about getting all down and dirty with messing and removing all your files or what not. But what I do is I just reformat my drive by reinstalling an Operating system over your current one.

If you are trying to clean everything up manually then it is probaly over my head as I am still in learning processes.

Hope this helps.


Thanks,

---

### Post by Quackers on 2010-09-23
I think the manufacturer of the hard drive will have such a tool. Alternatively, although I haven't actually used it, I believe the "Ultimate Boot CD" will do it.

---

### Post by rgiles43 on 2010-09-23
Hello,

I have searched the manufacturer website of both western digital and seagate HD's and have found that they have a disc utility wizard however seems like they only support it for windows software and not linux.

---

### Post by Joe of loath on 2010-09-23
Boot into a linux live CD, and type into a terminal:

```
sudo dd if=/dev/zero of=/dev/**your hard drive here, eg sda or hda**
```

Do it as many times as you feel are needed. It will take a while, but 3 should be sufficient.

---

### Post by stmurray on 2010-09-23
Although I haven't used it in several years, I always liked DBAN ([http://sourceforge.net/projects/dban/](http://sourceforge.net/projects/dban/)).  Boot from it, select options and go.  It will cleans all drives it finds, so never put it in a machine that has any disk with data you want.  Repartitioning, reformatting and/or installing a new OS do NOT wipe drives of data.  Also Note that DOD wipes can take a long time (as in days on really large drives to do multiple passes)

Also I believe the post above is correct that many new drives have the feature built-in, but I would just use DBAN.

---

### Post by Soul-Sing on 2010-09-23
i would def. use Dban. but not gutsy....:)

---

### Post by Andrew.Z on 2010-10-22
> **fidelandche said:**
> they say they wipe the hard drive to US Department of Defense standard 5220.22M.

[Using software to wipe a HDD to DOD 5220.22M is a myth](http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk) because DOD (2007) requires mechanical destruction or deguassing for media passing outside the DOD.

> 
 But I would feel a lot happier if I did it myself first, so how do I go about doing it?

Use DBAN or DD as suggested, but...

> **Joe of loath said:**
> Do it as many times as you feel are needed. It will take a while, but 3 should be sufficient.


[Recovery of data after one pass](http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk) is also an urban legend, so done properly, once is enough.  The only limit of using dd as suggested is it doesn't wipe the remapped bad sectors, which DBAN can do in a special mode.  Unless the hard drive is in bad shape, the remapped sectors usually contain little or no data.

---

