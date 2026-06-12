---
title: "How many formats can an image walk down?"
date: 2006-06-27
forum: General Help
---

### Post by keithjr on 2006-06-27
I always feel bad when I clutter something into the General forum, but I really don't know where else this fits...

I have a CD image file, in the format img/ccd/sub (the cloneCd trifecta), and I wish to mount it.  I've been told that I can simply use 

```

sudo mount -r loop -t iso9660 /placetomount /filetomount

```

to mount the image as if it were simply an .iso file, but this fails, telling me I've picked the wrong fs type.  If I try it without the type option, it tells me that I must select a type.  If I try to rename the file to *.iso, I get an error about a bad start block.  I will paste these in later when I get back to my own machine, but you get the idea.

I know there is a utility called ccd2iso which allegedly can do the conversion, but to build it I'd need an outdated version of automake (1.6).  My attempts to compile THAT failed as well (there is no package for 1.6), and as far as I can tell it would never work under Dapper.  Again, I can paste in the actual build errors if anybody cares.

So, does anybody know what, if and, filesystem type I can use to try to mount this file?  Or am I up a creek thanks to lack of backwards compability by multiple projects?

---

### Post by taurus on 2006-06-27
```

sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop <filename>.img /mnt/iso

```

---

### Post by christhemonkey on 2006-06-27
I think you *do* have to convert the image from ccd to iso.

As it says it needs an obsolete automake, i have found a workaround [here]("http://wiki.linuxquestions.org/wiki/CD_Image_Conversion#ccd2iso").


Basically, just download the source from [this site]("https://sourceforge.net/projects/ccd2iso") and then:
> cd src/

gcc -o ccd2iso ccd2iso.c 



Hope that helps.

---

### Post by keithjr on 2006-06-28
[QUOTE=christhemonkey]I think you *do* have to convert the image from ccd to iso.

As it says it needs an obsolete automake, i have found a workaround [here]("http://wiki.linuxquestions.org/wiki/CD_Image_Conversion#ccd2iso").


Basically, just download the source from [this site]("https://sourceforge.net/projects/ccd2iso") and then:




Hope that helps.[/QUOTE]



DINGDINGDINGDINGDING!

We have a winner! 

Thanks a million, good friend.  I owe you one.

---

### Post by christhemonkey on 2006-06-29
No problem!

---

### Post by Jenda on 2006-09-26
Umm... I'm trying to do this, but what do I do next?
1. get source, extract
2. cd ccd2iso/src/
3. gcc -o ccd2iso ccd2iso.c
But what next?

---

