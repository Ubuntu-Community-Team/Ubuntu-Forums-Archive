---
title: "File Renaming Program Wanted"
date: 2010-08-24
forum: General Help
---

### Post by alphaamanitin on 2010-08-24
Hello Forum.  

I know this is not a strictly Ubuntu request, but I was wondering if anyone knew of a free GNU program that will automatically rename all files in a folder.  I am pretty sure I could eventually write a perl script to do this (by eventually I mean in a few months of work at it), but I was hoping that some one knows one already or even better an easy way to do it in the BASH terminal.  

AlphaA

---

### Post by endotherm on 2010-08-24
I use pyrenamer in linux, though I can't gaurentee that RMS has blessed it himself.
in a pinch, if I need more options, ReNamer for windows runs flawlessly in wine. as for a script, much of the form of it would be determined by the name you want to set.

---

### Post by spjackson on 2010-08-24
> **alphaamanitin said:**
> 
I know this is not a strictly Ubuntu request, but I was wondering if anyone knew of a free GNU program that will automatically rename all files in a folder.  I am pretty sure I could eventually write a perl script to do this (by eventually I mean in a few months of work at it), but I was hoping that some one knows one already or even better an easy way to do it in the BASH terminal.  


Well, it depends what you want to rename them to. If it's simple like adding a prefix or suffix, then you can type this into a bash session.

```
user@host:~/tmp$ for f in *
> do
> mv "$f" "$f".old
> done
```which adds ".old" to all files (and/or folders) in the current directory.

---

### Post by DavePlummer on 2010-08-24
I like Metamorphose2, found at [http://file-folder-ren.sourceforge.net/](http://file-folder-ren.sourceforge.net/).

---

### Post by egalvan on 2010-08-24
I've used Bulk Rename (it's in the repos)

What I especially like about it is it's "interactive" nature...
you can see what the results will be. before having to commit to them.

---

### Post by alphaamanitin on 2010-08-25
Thanks for the replies guys.  I will definitely look into those.  And endotherm, thanks for also mentioning a windows program.  I need to rename about 17,000 files and am looking to just rename them 1-17,000.  Even though I marked this as solved, can anyone show me how to do that inside a directory in BASH?

Thanks,

AlphaA

---

### Post by spjackson on 2010-08-25
> **alphaamanitin said:**
> I need to rename about 17,000 files and am looking to just rename them 1-17,000.  Even though I marked this as solved, can anyone show me how to do that inside a directory in BASH?

Something like this:
```
#!/bin/bash

typeset -i name_counter=1
for file in *
do
    # No leading zeroes
    new_name=$name_counter
    # Use leading zeroes as NNNNN
    # printf -v new_name "%05d" $name_counter
    if [ -e $new_name ] ; then
        echo $new_name already exists
    else
        mv "$file" $new_name
    fi
    name_counter+=1
done
```Note that this will rename them 1-17000. If you want 00001-17000 then uncomment the printf line. If the target filename already exists, then the original file is not renamed.

---

### Post by inameiname on 2010-08-25
Renamer. This is the best. I use this all the time.

[http://gnome-look.org/content/show.php/Renamer?content=87601](http://gnome-look.org/content/show.php/Renamer?content=87601)

---

