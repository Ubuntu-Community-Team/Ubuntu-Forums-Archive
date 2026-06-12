---
title: "mount into a non empty folder"
date: 2010-07-19
forum: General Help
---

### Post by cym104 on 2010-07-19
i need to do the following things and googling didn't help much:
 
1.mount a volume(or windows share, whatever) into a non empty folder
2.both the original content of the folder and the content of the newly mounted volume is accessible
3.updated and newly created files can be written to the mounted volume or the original folder determined by something like a switch at mount time
4.if files with same names exist both in the folder and on the volume, then which file to be presented to the OS is determined by their last modified date/time.
 
any one can give a walk-through on how to achieve this?

---

### Post by hawthornso23 on 2010-07-19
What you are asking is very specific and I don't know if mount works that way. I think you might get better answers if you go back a step and explain why you want to do this. There may be another way to do what you want to do.

---

### Post by The Cog on 2010-07-19
I don't believe this is possible. The nearest thing is **unionfs** but it doesn't meet your criteria for using the datestamp for priority when the same filepath exists on both sources.

---

### Post by cym104 on 2010-07-19
> **hawthornso23 said:**
> What you are asking is very specific and I don't know if mount works that way. I think you might get better answers if you go back a step and explain why you want to do this. There may be another way to do what you want to do.
it dosen't have to be done by using only "mount", if u know any 3rd party apps that is capable of doing it, just post ~~;)

---

### Post by valbaca on 2010-07-19
Try the following, where "dir" is the directory you would like to use:
```
mount --make-shared dir
```
 
man mount can provide more information. For an online version of man pages, try this [http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

---

### Post by cym104 on 2010-07-19
> **valbaca said:**
> Try the following, where "dir" is the directory you would like to use:
```
mount --make-shared dir
```
 
man mount can provide more information. For an online version of man pages, try this [http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)
 I'v read the page and it seems like this's nothing even near what I'm looking for~~

---

