---
title: "Automatic file sorting"
date: 2011-09-07
forum: General Help
---

### Post by BLazerboy65 on 2011-09-07
I have been attempting to create a Bash script which would sort files into folders based on file extension, but to no avail. How would I write a script which could do this, and maybe even do it automatically when a new file is detected?

---

### Post by kerry_s on 2011-09-07
come on man details, no 1 can write a script for you if they don't have the info. what kind of files? moved where? etc...

it's simple enough, something like:
```
#!/bin/sh

mv /some/folder/*.doc /some/other/folder
mv /some/folder/*.pdf /some/other/folder
etc...

exit 0
```

---

### Post by BLazerboy65 on 2011-09-08
I want to know how to make a script which will dynamically find all the different file extensions in a folder, create subfolders whose names are the file extensions which will go into them, and then move the files into the folder named their file extension.

---

### Post by kerry_s on 2011-09-08
how about i just give you the commands & you put it together.

find file extensions:
```
ls | grep -Eo "\..+" | sort -u | sed s'/\.//g'
```

make a folder:
```
mkdir /$whatever
```

move them:
```
mv /here /to/there
```


```
mkdir $PWD/$(ls | grep -Eo "\..+" | sort -u | sed s'/\.//g')
```
will make the folders, i can't figure out the mv command to get the different files to the right folder.

---

### Post by nothingspecial on 2011-09-08
My attempt at it would be this,

To test it I create some files
```

$ touch {1,2,3,4,5}.{mp3,jpg,txt}
$ ls
1.jpg  1.mp3  1.txt  2.jpg  2.mp3  2.txt  3.jpg  3.mp3	3.txt  4.jpg  4.mp3  4.txt  5.jpg  5.mp3  5.txt
```

Then using parameter expansion to catch the extensions, create the directories if they don't exist and move the files there.


```
for f in * 

do if [[ ! -d "${f##*.}" ]] 
then mkdir "${f##*.}";
fi  

mv -u "$f" "${f##*.}";  done




```

which works
```
$ ls -R
.:
jpg  mp3  txt

./jpg:
1.jpg  2.jpg  3.jpg  4.jpg  5.jpg

./mp3:
1.mp3  2.mp3  3.mp3  4.mp3  5.mp3

./txt:
1.txt  2.txt  3.txt  4.txt  5.txt
```

although I'm sure a certain someone will be along later to point out the glaring errors. :-\"

---

### Post by BLazerboy65 on 2011-09-08
Is there way to make it only attempt to sort files and not folders?

---

### Post by nothingspecial on 2011-09-08
I don't understand what you mean. It goes through the files, creates folders based on the extension and puts the files in the relevant folder.

What do you mean by sort files and not folders?

---

### Post by BLazerboy65 on 2011-09-08
I had some folders which had version numbers in their names, and this script put the folder into other folders which were named last part of the version number.

---

### Post by nothingspecial on 2011-09-08
Ah, I didn't realise you had folders already.

In that case you need to add a test to see whether or not something in that folder is a file.
```

for f in *

do if [[ ! -d "${f##*.}" ]] 
then mkdir "${f##*.}"
fi
 [COLOR="Red"]
if [[ -f "$f" ]] [/COLOR]
then  mv -u "$f" "${f##*.}"
fi
  
done
```

See if that works. I assumed this was a one time job, am I right in thinking you want to run this periodically?

---

### Post by sisco311 on 2011-09-08
I'd go with something like:
```

for f in *
do 
    if [[ -f "$f" ]] 
    then
        dest="${f##*.}"
        # resume the next iteration if directory can't be created
        # no need to test if it exist; let -p do its job ;)
        mkdir -p "$dest" || continue
        mv -u -- "$f" "$dest"
    fi
done
```

---

### Post by ninjaaron on 2011-09-08
I'm pretty sure the first reply in this thread would do it.

What you are asking is basically the easiest thing in the world to do with a script.

---

### Post by nothingspecial on 2011-09-08
> **ninjaaron said:**
> I'm pretty sure the first reply in this thread would do it.



No it wouldn't, well it would if you wrote a script infinitely long, with a line containing every possible combination of letters and numbers that could make up a file extension (which is infinite). A file extension can be anything 

file.tre5r79u9fgcfxer46i8o

With what I attempted, and sisco did properly, it doesn't matter what the file extension is.

---

### Post by kerry_s on 2011-09-08
> **ninjaaron said:**
> I'm pretty sure the first reply in this thread would do it.

What you are asking is basically the easiest thing in the world to do with a script.

well he complicated it with creating folders then moving the files to the right folders. if he had narrowed done just the 1's he wants to work with it would be easier. it's like having the script create it's own script, the linux ai. :lolflag:

i was to tired yesterday, trying to do it in 1 liners's & cover all the bases.

i think "nothingspecial" has got a good grip on this, so i'm going to leave it to him. :)

---

### Post by BLazerboy65 on 2011-09-08
Yes, I would like to run it whenever I need to sort out files.

---

