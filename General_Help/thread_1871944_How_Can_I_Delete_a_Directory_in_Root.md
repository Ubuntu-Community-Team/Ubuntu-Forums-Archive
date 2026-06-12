---
title: "How Can I Delete a Directory in Root?"
date: 2011-10-29
forum: General Help
---

### Post by w201 on 2011-10-29
How can I delete a directory with files in it? **sudo rm** gives me rm: **cannot remove... Is a directory**

---

### Post by haqking on 2011-10-29
> **w201 said:**
> How can I delete a directory with files in it? **sudo rm** gives me rm: **cannot remove... Is a directory**

what is the directory and why one in root ? be careful what you do as sudo especially folders you need use sudo to remove

however


```
man rm
```

---

### Post by w201 on 2011-10-29
They're just files from another OS that I was trying to double-boot, but I don't need it anymore so it should be safe to delete.

So should **rm -r** work?

---

### Post by haqking on 2011-10-29
> **w201 said:**
> They're just files from another OS that I was trying to double-boot, but I don't need it anymore so it should be safe to delete.

So should **rm -r** work?

yes i would refer you to the man pages however to make sure you understand

---

### Post by lisati on 2011-10-29
> **haqking said:**
> yes i would refer you to the man pages however to make sure you understand

Agreed. I could put up another command similar to the one suggested by w201, but it can cause serious damage to someone's computer if there's a typo.

---

### Post by w201 on 2011-10-29
Thanks, I'll read up on the rm info on the man pages. 

I'm a 100% certain that it was safe to remove those files so I used the rm -r command, thanks for that too.

---

### Post by w201 on 2011-10-29
Guys, I read the section on rm but I'm still unclear on why rm didn't work but rm -r did. Maybe I'll read the thing over one more time, but is there any light you can shed on that?

---

### Post by oldos2er on 2011-10-29
rm -r means recursive delete. From man rm:  By default, rm does not remove directories.  Use the --recursive (-r or -R) option to remove  each  listed  directory, too, along with all of its contents.

---

### Post by w201 on 2011-10-29
Gotcha. So if I'm 100% positive that a deleting a specific directory won't harm my computer than it's safe to use rm -r?

I can see typos being a problem but I double checked my spelling.

---

### Post by oldos2er on 2011-10-29
Yes. Use Tab completion to cut down on typos.

---

### Post by w201 on 2011-10-29
> **oldos2er said:**
> Yes. Use Tab completion to cut down on typos.

Thanks! That's a nice little feature I didn't know existed.

---

### Post by haqking on 2011-10-29
> **w201 said:**
> Thanks! That's a nice little feature I didn't know existed.

Just so you know why we were careful with advice.

read here at 3rd post by jdong

[http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

---

### Post by Slim Odds on 2011-10-29
rmdir

---

### Post by haqking on 2011-10-29
> **Slim Odds said:**
> rmdir

see OP.

The folder has files in it. rmdir ony works if dir is empty which is why we said rm-r

see

```
man rmdir
```

---

### Post by w201 on 2011-10-29
> **haqking said:**
> Just so you know why we were careful with advice.

read here at 3rd post by jdong

[http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

I appreciate the careful advice. That's an interesting post. I'll definitely try to stay away from those commands until I have more experience :D

---

### Post by w201 on 2011-10-29
I almost forgot to ask, but there are two files on my root directory:

**vmlinuz** and **initrd.img**

I think they were part of that directory I deleted but somehow ended up outside of the directory in root. Do you guys know if these files are safe to delete?

***EDI***

there's actually duplicate files. So there are the two I mentioned and two more:
**vmlinuz.old** and **initrd.img.old**

---

### Post by haqking on 2011-10-29
> **w201 said:**
> I almost forgot to ask, but there are two files in my root drive:

**vmlinuz** and **initrd.img**

I think they were part of that directory I deleted but somehow ended up outside of the directory on the root drive. Do you guys know if these files are safe to delete?

vmlinuz is your linux kernel....LOL

initrd is an initial ramdisk

no dont delete and you cant when the system is mounted anyways

why are trying to delete things which you dont know what they are ? LOL

---

### Post by w201 on 2011-10-29
> **haqking said:**
> vmlinuz is your linux kernel....LOL

initrd is an initial ramdisk

no dont delete and you cant when the system is mounted anyways

why are trying to delete things which you dont know what they are ? LOL

LOL. Well I'm still new to linux and still learning, but the  directory you guys helped me to delete had to go because it was taking up 5 gigs of space on my drive. I put that directory in root myself so I was sure the system was not dependent on it to operate.

Why are the two files duplicate? Read the last part of post #16

---

