---
title: "&quot;Places&quot; don't work"
date: 2009-09-11
forum: General Help
---

### Post by geohei on 2009-09-11
Hi.

Freshly installed 9.04.

When I go on Places > (anything = Home Folder, Desktop, Documents, ...), the respective folder doesn't open. The mouse pointer shows busy for a while and that's it. No window opens.

Why is that?

Thanks,

---

### Post by prshah on 2009-09-11
> **geohei said:**
> 
When I go on Places > (anything = Home Folder, Desktop, Documents, ...), the respective folder doesn't open.

There was a small bug similar to this a while back; try [this solution]("http://ubuntuforums.org/showthread.php?p=6082327#post6082327") and see if it helps.

It may also help to go through the entire thread.

---

### Post by geohei on 2009-09-21
I read the thread now. I don't use nautilus. It's plain 9.04 Desktop out of the box.

Also ... Places > Computer doesn't open. Hence your suggestion doesn't work for me :(.

Thanks,

---

### Post by Witepa on 2009-09-21
9.04 desktop out of the box uses nautilus for it's file browser, you are using it.

---

### Post by geohei on 2009-09-21
#&%$ sorry. newbie! ;((

I tested 9.04 in a VM and Places > ... works perfectly there.

I have no clue why it doesn't on my partitioned installation?

---

### Post by wojox on 2009-09-21
Can you enter your home directory?

---

### Post by geohei on 2009-09-21
Not via Places > Home Folder. I get a busy mouse pointer for about 15 seconds, then nothing!

The home folder exists of course (checked in terminal).

BTW ... if I say "nautilus-file-management-properties", I set "Segmentation fault".

... later ...

BTW2 ... what's going on here?
```
root@ubuntu904hol:/home/geohei# nautilus
Segmentation fault
```

---

### Post by geohei on 2009-09-26
I read this here:
[http://en.wikipedia.org/wiki/Segmentation_fault]("http://en.wikipedia.org/wiki/Segmentation_fault")

How is it possible that starting nautilus produces a segmentation fault?

Is the partition corrupt for some reason?

Thanks,

---

### Post by ecmatter on 2009-09-26
> 
How is it possible that starting nautilus produces a segmentation fault?


Do you have a blank cd or dvd in your cd/dvd drive?  If you do, remove it and try to open nautilus again.

Also: is there any particular reason to be logged in as root?

---

### Post by wojox on 2009-09-26
Try this:

Alt+F2

In the text box type 

```
/home/<username>
```Of course substituting your name for <username>

Then press run. Tell me if that opens your home folder.

---

### Post by geohei on 2009-11-27
> **ecmatter said:**
> Do you have a blank cd or dvd in your cd/dvd drive?  If you do, remove it and try to open nautilus again.

Also: is there any particular reason to be logged in as root?
Thanks a lot !!!
There as a CD in the drive (not empty though). After removing it, "Places" worked fine! Great!

Yes, root was just for troubleshooting permissions. Normally I work as "normal" user.

---

