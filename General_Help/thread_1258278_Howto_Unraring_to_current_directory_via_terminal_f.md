---
title: "Howto Unraring to current directory via terminal from other directory?"
date: 2009-09-04
forum: General Help
---

### Post by grantjohnston on 2009-09-04
I've found the 

```
find -name .*.rar -exec unrar e {} \;
```

variation, but what I need is a bit different. I need it unrar'd to the current directory, but the .rars are in another directory.

Or, if I could unrar from the current Directory and export them to other directory that would work just fine as well.


I've been doing them all manually with 

```
unrar e */directory name/filename.part01.rar*
``` and it puts it in the current directory, but I was wondering if there was an easier way, as there's about 30 different .rars with 15-30 parts to each per folder.


Like I said, I had been looking and had only found the unrar from current to current directory.

Thanks for the help in advance,


Grant

---

### Post by grantjohnston on 2009-09-05
bump..

I'm sure this can be done and I'm just missing some minute alteration of the command, but I still can't find anything.


Anyone?

---

### Post by grantjohnston on 2009-09-06
/sigh. This sucks doing them individually guys, does nobody have a clue how to do it? I'm SURE there is a way, I just can't tell from reading the man page from it. Somebody please help!!!


Again, thanks in advance



Grant

---

### Post by Lampi on 2009-09-06
> **grantjohnston said:**
> filename.part01.rar
this sounds like you split/span the rar archive over several files. If so, you can all place them in the same folder and unpack it like this:
```
tar -xvf filename.part01.rar <target directory>
```
it will run an integrity check first, to make sure all archive parts are available and intact, after that it will unpack the files.

---

### Post by grantjohnston on 2009-09-06
> **Lampi said:**
> this sounds like you split/span the rar archive over several files. If so, you can all place them in the same folder and unpack it like this:
```
tar -xvf filename.part01.rar <target directory>
```
it will run an integrity check first, to make sure all archive parts are available and intact, after that it will unpack the files.



That's just how the files came when I downloaded them, I didn't create the .rars. They're in a folder in my home directory and i need the contents unpacked in a folder on an external that's attached to the box. Right now I just have my directory on the terminal pointed to the external so it just extracts to the local folder which just happens to be where I want it.

---

### Post by grantjohnston on 2009-09-07
Sorry.... Bump again. Hate doing this, but I also hate doing the single archive unraring....

---

### Post by andrew.46 on 2009-09-12
Hi grantjohnson,

> **grantjohnston said:**
> I didn't create the .rars. They're in a folder in my home directory and i need the contents unpacked in a folder on an external that's attached to the box. 

It could be scripted or done with a for loop easily enough. What sort of files are extracted from the rar files?

Andrew

---

