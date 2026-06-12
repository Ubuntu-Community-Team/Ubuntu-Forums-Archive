---
title: "Renaming Bulk Files"
date: 2012-02-24
forum: General Help
---

### Post by w201 on 2012-02-24
Hey guys- what's the best command to rename bulk files? 

For example, in a directory, I have a list of jpg images, all named photo(1).jpg, photo(2).jpg, photo(3).jpg, etc... I want to give them meaningful names.

The way I've been going about it so far is to  issue ```
mv photo\(1\).jpg landscape_1.jpg
``` for each photo. Can become a bit time consuming when I have multiple images.

I did find this in another site: ```
ls * | sed -e 'p;s/foo/bar/' | xargs -n2 mv
```

I don't understand it, just wondering if there's an easier way? Thanks!

---

### Post by iponeverything on 2012-02-24
do a man on the "rename" command. It is what you are looking for.

---

### Post by Thorsen V on 2012-02-24
depends how sophisticated you want it to be:

If ALL the files in the dir are jpgs then one of the simplest methods is:

$ j=1; for i in *; do echo mv $i landscape_$j.jpg; j=$[j+1] ;  done

NOTE: the "echo" gives a preview of the result ... if it looks okay take the echo out and run the command again to do the actual move ...

---

### Post by w201 on 2012-02-24
> **iponeverything said:**
> do a man on the "rename" command. It is what you are looking for.

Thanks! I've been doing man on the wrong term (mv)

Thorsen V, I appreciate your suggestion.

---

### Post by Thorsen V on 2012-02-24
A slight improvement if you have hundreds of sequential files to rename:

$ j=1; for i in *.jpg; do echo mv $i `printf landscape_%04d.jpg $j`; j=$[j+1] ;  done

This produces outputs with up to 4 leading zeros[INDENT]landscape_0001.jpg
landscape_0002.jpg
etc ..
landscape_0010.jpg
...
landscape_0100.jpg
...
landscape_9999.jpg

[/INDENT]Change the specifier "%04d"  to suit your needs

---

### Post by Thorsen V on 2012-02-25
That one liner is actually very neat if your files are already numbered:

$ ls *
photo1.jpg  photo2.jpg  photo3.jpg  photo4.jpg

$ ls * | sed -e 'p;s/photo/landscape/'| xargs -n2 mv

$ ls *
landscape1.jpg  landscape2.jpg  landscape3.jpg  landscape4.jpg

I'll have to add that to my collection :)

---

