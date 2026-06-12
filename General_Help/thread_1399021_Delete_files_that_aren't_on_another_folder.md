---
title: "Delete files that aren't on another folder"
date: 2010-02-05
forum: General Help
---

### Post by sombrancelha on 2010-02-05
Hello,

I've been organizing my pictures (i.e. deleting the bad ones). However, I've recently got hold of those same pictures on a higher resolution and I'd like to delete the same pictures of the higher resolutions.

This means that I'll have two folders, *High Res* and *Low Res*. I'd go through all files in the *High Res* folder and I'll check if there's a file with the same name in the *Low Res* folder. If there is, the file in the *High Res* folder will be kept. Otherwise, I'll delete it.

For example:

In folder High Res, I have:
PIC1.JPG
PIC2.JPG
PIC3.JPG
PIC4.JPG
PIC5.JPG

In the folder Low Res (already deleted the bad ones), I have:
PIC2.JPG
PIC5.JPG

So I wanted some quick way to delete PIC1.JPG, PIC3.JPG and PIC4.JPG from the High Res folder.

Thanks

---

### Post by john newbuntu on 2010-02-05
Try something like the following.  Please test this thoroughly before running it

comm -2 -1 <(ls ~/Highres/) <(ls ~/Lowres/) | xargs -ti rm ~/Highres/{}

---

### Post by sombrancelha on 2010-02-08
It did exactly the opposite of what I need: it deleted that files that were on the Lowres folder. But it should delete the files that AREN'T on that folder.

---

### Post by jamesisin on 2010-02-08
My guess would be to modify it thusly:

```
comm -2 -1 <(ls ~/Highres/) <(ls ~/Lowres/) | xargs -ti rm ~/Lowres/{}
```

---

### Post by sombrancelha on 2010-02-08
> **jamesisin said:**
> My guess would be to modify it thusly:

```
comm -2 -1 <(ls ~/Highres/) <(ls ~/Lowres/) | xargs -ti rm ~/Lowres/{}
```

Nope.
This deletes the files on the Lowres folder.

---

### Post by jamesisin on 2010-02-08
So you want to compare the list and keep only those files which appear in both lists?

---

### Post by sombrancelha on 2010-02-08
> **jamesisin said:**
> So you want to compare the list and keep only those files which appear in both lists?

Exactly.

---

### Post by jamesisin on 2010-02-08
Try this one:

```
comm -3 <(ls ~/Highres/) <(ls ~/Lowres/) | xargs -ti rm ~/Lowres/{}
```

---

### Post by golanbatrac on 2010-02-08
nevermind.

---

### Post by septekin on 2010-02-09
You may try:

```
rsync -rv --delete ~/Lowres/ ~Highres/
```

---

### Post by kaibob on 2010-02-09
> **jamesisin said:**
> Try this one:

```
comm -3 <(ls ~/Highres/) <(ls ~/Lowres/) | xargs -ti rm ~/Lowres/{}
```

I'm not familiar with the comm command, but shouldn't the directory after rm be Highres?

---

### Post by jamesisin on 2010-02-09
> **septekin said:**
> You may try:

```
rsync -rv --delete ~/Lowres/ ~Highres/
```

Probably not a good choice since the files contained in the folders have the same names yet different contents.  Rsync will want to conform those samed-named files to files with the same contents.

---

### Post by jamesisin on 2010-02-09
> **kaibob said:**
> I'm not familiar with the comm command, but shouldn't the directory after rm be Highres?

Judging from the man page for comm, the -3 option will parse out the files not present in both directories.  If that is the case, I'm not clear it will matter which directory is specified in the next command, but you may be correct.

---

### Post by septekin on 2010-02-09
jamesisin;

thanks for your concern. However, I tried the rsync on files with completely different contents and it worked.

---

### Post by septekin on 2010-02-09
I stand corrected! rsync does work but replaces the two highres files with lowres versions: not what is wanted. My apologies.

---

### Post by septekin on 2010-02-09
Thist may or may not be of interest:

I took seven .JPG files from my collection. Renamed the first five pic1.JPG .. pic5.JPG and placed them in /Highres folder. Renamed the remaining two pic2.JPG and pic5.JPG and placed them in /Lowres folder.

I gave the following command:

> rsync -rv --delete --ignore-existing ~/Lowres/ ~/Highres/

pic1.JPG, pic3.JPG and pic4.JPG were deleted in /Highres. pic2.JPG and pic5.JPG in /Highres remained as they were.

---

### Post by kaibob on 2010-02-09
> **jamesisin said:**
> Judging from the man page for comm, the -3 option will parse out the files not present in both directories.  If that is the case, I'm not clear it will matter which directory is specified in the next command, but you may be correct.

I'm sorry--I didn't explain properly.

I ran a test by creating a ~/Highres directory with five files named pic1.JPG, pic2.JPG, pic3.JPG, pic4.JPG, and pic5.JPG. I then created a ~/Lowres directory with two files named pic2.JPG and pic5.JPG. 

Next, I ran the following command and received a series of file-not-found error messages:

```
comm -3 <(ls ~/Highres/) <(ls ~/Lowres/) | xargs -ti rm ~/Lowres/{}
```

I changed the above command by substituting Highres for Lowres after the rm command and then ran the command again. The files, pic1.JPG, pic3.JPG, and pic4.JPG, were deleted from the Highres directory, which is what I understand the OP wanted. 

```
comm -3 <(ls ~/Highres/) <(ls ~/Lowres/) | xargs -ti rm ~/Highres/{}
```

So, I think your command works fine except that it attempts to delete the unwanted files from the wrong directory.

---

### Post by jamesisin on 2010-02-09
Excellent work, kaibab.  Looks like this should do it then:

```
comm -3 <(ls ~/Highres/) <(ls ~/Lowres/) | xargs -ti rm ~/Highres/{}
```

Unless he is trying to delete from *both* directories; in which case he will want to use each command in succession.

---

