---
title: "Bash script...ooops"
date: 2011-12-14
forum: General Help
---

### Post by Bromden on 2011-12-14
Hi guys, I'm trying to put a bit of order inside a folder.
I've tried this bash script:


```
find -iname "Lesson #008*" -exec mv {} ~/Downloads/FOLDER \;  
```

It makes something but I don't understand exactly what XD
I just wanted to find and move the found files, but instead moving the files, it makes them disappear... @_@

1)Where have been moved the files?
2)How should I correct the script?

Thank you!

---

### Post by TeoBigusGeekus on 2011-12-14
Use cp instead, to make sure you won't lose any data (you can delete it later) and quote the braces:
```
find -iname "Lesson #008*" -exec cp "{}" ~/Downloads/FOLDER \;
```

---

### Post by Bromden on 2011-12-14
Yeah! Did it!

Here is the code!


```
find .  -iname "wordstosearch1*" | xargs -i mv "{}" ./FOLDER1
```

Now i just need to make the numbers advance automatically

---

### Post by TeoBigusGeekus on 2011-12-14
> **Bromden said:**
> It still doesn't copy anything into the folder :\

Oh yes, of course: you don't specify where to look for the files. So, if you want it to search in your home folder, for example, use:
```
find ~/ -iname "Lesson #008*" -exec cp "{}" ~/Downloads/FOLDER \;
```
Replace ~/ with the desired search path.

---

### Post by nothingspecial on 2011-12-14
Also, you need to be careful with find if you don't understand what it is going to do. If all the files are in one folder, it is unnecessary anyway. 

What exactly are you trying to do?

---

### Post by Bromden on 2011-12-14
> **nothingspecial said:**
> Also, you need to be careful with find if you don't understand what it is going to do. If all the files are in one folder, it is unnecessary anyway. 

What exactly are you trying to do?

Succesful

Here is the code! :p


```
find .  -iname "wordstosearch1*" | xargs -i mv "{}" ./FOLDER1
```


Now i just need to make the numbers advance automatically.
I mean this:

find file 1 and copy it in folder 1
find file 2 and copy it in folder 2
find file 3 and copy it in folder 3
...

```
find .  -iname "wordstosearch{1..100}*" | xargs -i mv "{}" ./FOLDER{1..100}
```

I tried this but doesn't works...

---

### Post by Bromden on 2011-12-15
Ok I've made a working Bash script to move a large number of files into their respective folder.

Here it is :guitar:

```
#!/bin/bash
COUNT=100
# bash until loop
until [ $COUNT -gt 170 ]; do
		find  ~/Downloads/FOLDER  -iname "Beginner Lesson #$COUNT*" | xargs -i mv "{}" ~/Downloads/FOLDER/foo$COUNT
		echo Value of count is: $COUNT
        let COUNT=COUNT+1
done 
```

Fortunately i'm not using Winzoz :-)

---

