---
title: "How to move a file matching *.ext regardless of case"
date: 2010-01-26
forum: General Help
---

### Post by bwitherell on 2010-01-26
Hi,

Can anyone tell me how I can use the mv command to move a file that matches *.ext regardless of the case?

I would like to be able to move:

*.ext
*.EXT
*.ExT

....and so on with a single command. I do not want to have to type out all combinations of this single file extension in my script because my file system is case sensitive.

any help is much appreciated.

---

### Post by tors on 2010-01-26
Maybe you could use the command "find" to help you.

> find /old/directory -iname "*.ext" -exec mv {} /new/directory \;


("-iname" is for ignore case)

---

### Post by bwitherell on 2010-01-26
That helps a lot thanks!

That did the trick. I do get an error message about all the files being the same file though even though their name are completely different.

That does not matter to me though because it did move the files. 

Thanks a lot! you helped me out of a bind.

---

### Post by tors on 2010-01-26
Excellent!


Ah, yes. You will get error messages if you move the files into the directory where find is running as it will find the newly moved files and try to move them again (they also match "*.ext").

---

### Post by bwitherell on 2010-01-26
I assume that would apply to moving files into a sub directory of the directory find is running in. In other words it seems to find recursively.

---

### Post by tors on 2010-01-26
Yes indeed. With this new knowledge, the command could maybe be modified:

> find /old/directory -maxdepth 1 -iname "*.ext" -exec mv {} /old/directory/subdirectory \;

---

### Post by sisco311 on 2010-01-26
```
mv *.[eE][xX][tT] /new/dir
```should also work.

---

### Post by bwitherell on 2010-01-26
Awesome! very helpful thanks again.

---

### Post by bwitherell on 2010-01-26
> **sisco311 said:**
> ```
mv *.[eE][xX][tT] /new/dir
```should also work.

This seems like an even more simple approach. Thank you both for the help. The find command will be very useful for me in renaming some other files so both a very big help.

Thanks!

---

### Post by jamesisin on 2010-01-26
It might be possible to, at the same time, replace the extensions so they conform.

Would a replacement like this work?

//.[eE][xX][tT]/.ext

---

### Post by bwitherell on 2010-01-26
> **jamesisin said:**
> It might be possible to, at the same time, replace the extensions so they conform.

Would a replacement like this work?

//.[eE][xX][tT]/.ext

That is a great idea. Thanks for the help i will give it a shot.

---

### Post by sisco311 on 2010-01-26
```
for file in *.[eE][xX][tT]; do 
  mv "$file" new/path/"${file//.???$/.ext}"
done
```

---

### Post by kaibob on 2010-01-26
The other answers are probably easiest, but another option is the nocaseglob shell option. For example, the following moves file.ext, file.EXT and file.eXt.

```
shopt -s nocaseglob ; mv  *.ext /target/directory
```

---

### Post by jamesisin on 2010-01-26
Thanks, sisco311.  That's exactly what I meant.

---

### Post by kaibob on 2010-01-26
> **sisco311 said:**
> ```
for file in *.[eE][xX][tT]; do 
  mv "$file" new/path/"${file//.???$/.ext}"
done
```

I believe there may be a typographical error in the above command, as it does not appear to work (or at least wouldn't work for me). Removing the $ after .??? fixed things. An alternative that may be what sisco311 intended is:

```
mv "$file" "/new/path/${file/%.???/.ext}"
```

---

### Post by 3rdalbum on 2010-01-26
Thanks for the suggestion of using [eE][xX][tT] - it's actually just helped me make one of my programs less clunky!

---

### Post by jamesisin on 2010-01-27
> **kaibob said:**
> ```
mv "$file" "/new/path/${file/%.???/.ext}"
```

Yeah, that's right.  The % means 'at the end of the filename/string', the dot is literal, and the ? means 'any single character'.

---

### Post by sisco311 on 2010-01-27
> **kaibob said:**
> I believe there may be a typographical error in the above command, as it does not appear to work (or at least wouldn't work for me). Removing the $ after .??? fixed things. An alternative that may be what sisco311 intended is:

```
mv "$file" "/new/path/${file/%.???/.ext}"
```

Thanks for the correction!

---

