---
title: "external hard drive is read only"
date: 2012-02-27
forum: General Help
---

### Post by tylerauger on 2012-02-27
i use an external hard drive to keep my movies on to watch on my xbox. i went to add a movie and it says error desination is read only. i am the owner and it says it is a read only filesystem. when i ran smart data and the only red flag is reallocated sector count. i plugged it into my windows machine and ran chkdsk it said it fixed it. i guess it didnt. i had no problems with it yesterday. it is ntfs file system and i am running ubuntu 11.10. any help is appreciated thanks

---

### Post by 23dornot23d on 2012-02-27
You have to make sure its unmounted properly from leaving Windows .... that was something that I have seen come up a few times before ......

But if it mounts in read only mode .... is it due to windows not un-mounting it properly

You may need to look at this first ..... so go into windows unmount the drive then try
it in Linux .... see if it makes a difference.

---

### Post by audiomick on 2012-02-27
> **23dornot23d said:**
> You have to make sure its unmounted properly from leaving Windows .....

I think this is true, but I think you have to run the windows disk repair thing on it. I think that is chkdsk.

[http://en.wikipedia.org/wiki/Chkdsk](http://en.wikipedia.org/wiki/Chkdsk)

---

### Post by tylerauger on 2012-02-28
Thanks for your reply. went into windows, ran the chkdsk again and safely removed it. but the problem still persists... and the disk utility errors in ubuntu remains the same. also chkdsk didnt find any errors this time.

---

### Post by tylerauger on 2012-02-28
i also put it into windows and ran the error checking function that checks specifficly for bad sectors. it ran all night and completed. i properly ejected it. but nothing changed...

---

### Post by Mark Phelps on 2012-02-28
This used to have something to do with NTFS problems -- don't know if it's still needed.

Check to see if you have ntfs-3g installed.  From what I recall, 11.10 installs ntfsprogs, which used to conflict with ntfs-3g.

If you don't have ntfs-3g installed, try installing it.  IF it complains about conflicts with ntfsprogs, remove that and install ntfs-3g.

---

### Post by tylerauger on 2012-03-01
it installed without issues but it didnt change anything

---

### Post by tylerauger on 2012-03-05
but since it was read only i gave up fighting with it. just copyied everything i could fit onto my internal hdd and formatted it. works like a charm now

---

