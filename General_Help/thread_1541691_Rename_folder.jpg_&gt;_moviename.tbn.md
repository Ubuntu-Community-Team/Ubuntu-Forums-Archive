---
title: "Rename folder.jpg &gt; moviename.tbn"
date: 2010-07-29
forum: General Help
---

### Post by rocker9455 on 2010-07-29
Hi All,
I want to rename my film collection's thumbnails from folder.jpg to 'moviename'.tbn and duplicate that and have it renamed to movie.tbn

My folder structure is set out like this
Media HD:
> Film name folder
> Film.avi with folder.jpg 
So i have about 150 folders which i need to rename folder.jpg in
Any help would be greatly appreciated!
Thanks,
Will

---

### Post by rubylaser on 2010-07-29
Create a new file called mover.sh and paste this...
```
# !/bin/bash
find . -type d | \
while read filename
do
filename=${filename%}
      cp "$filename"/folder.jpg "$filename"/movie.tbn
      mv "$filename"/folder.jpg "$filename"/"$filename".tbn
done
```

Put this into the directory that contains your movie folders.  You'll get 2 lines of errors when you run this,  because it will try to perform this action on the current directory, which will fail, but this will do it for you.

---

### Post by rocker9455 on 2010-07-29
> **rubylaser said:**
> Create a new file called mover.sh and paste this...
```
# !/bin/bash
find . -type d | \
while read filename
do
filename=${filename%}
      cp "$filename"/folder.jpg "$filename"/movie.tbn
      mv "$filename"/folder.jpg "$filename"/"$filename".tbn
done
```

Put this into the directory that contains your movie folders.  You'll get 2 lines of errors when you run this,  because it will try to perform this action on the current directory, which will fail, but this will do it for you.
Thanks awfully! It worked a treat, I don't suppose you have any idea where i can find a good tutorial/guide to learn to use bash?

Thanks

---

### Post by rubylaser on 2010-07-29
No problem, glad it worked for you.  Here's a good place to start...
[http://www.gnu.org/software/bash/manual/bashref.html]("http://www.gnu.org/software/bash/manual/bashref.html")

---

