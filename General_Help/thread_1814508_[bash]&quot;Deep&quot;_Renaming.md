---
title: "[bash]&quot;Deep&quot; Renaming?"
date: 2011-07-29
forum: General Help
---

### Post by blenderfox on 2011-07-29
Is there a way I can do a "deep" renaming of files?

For example, I can do this:

rename 's/\.JPG$/.jpg/' *.JPG

to rename all files ending with ".JPG" to ".jpg", but this only works in the current directory. How can I make this recursive? There's not a flag (that I can see) that does this. Basically, I want to rename ALL files on my hard drive with an upper case JPG extention to make them have a lower case jpg extention.

---

### Post by nothingspecial on 2011-07-29
Be careful with this, there may be files that you don't want to do this to, although you can use the -n flag for rename.

If by hard drive you mean an external hard drive please change ~/ for the path to your external (eg /media/data).

If you mean the entire system, change ~/ to / but really handle with care.

```
for f in $(find ~/ -type f -name *.JPG); do rename [COLOR="Red"]-n[/COLOR] 's/\.JPG$/.jpg/' "$f"; done
```

If you are happy, remove the -n (in red)

Like I said already, if you make a typo with find it can really mess things up. You have been warned.

---

### Post by AlphaLexman on 2011-07-29
Add the 'find' command to the beginning and use the execute command option of 'find'...

```
find . -name "*.JPG" -exec rename 's/\.JPG$/.jpg/' "*.JPG" {} +
```

**EDIT:** beat by nothingspecial

---

### Post by blenderfox on 2011-07-29
Thanks for the help. Both worked :)

---

### Post by blenderfox on 2011-07-30
> **AlphaLexman said:**
> Add the 'find' command to the beginning and use the execute command option of 'find'...

```
find . -name "*.JPG" -exec rename 's/\.JPG$/.jpg/' "*.JPG" {} +
```

**EDIT:** beat by nothingspecial

Just wondered, what does the {} and + mean at the end of the line?

---

### Post by pieroxy on 2011-07-30
I don't know for the +, but the {} is replaced by the file name in each execution. 

I usually end my "-exec" with "\;" so I guess the + is equivalent. It is here to notify find that the command parameter to the "-exec" flag is done. You need to put it there at the end of the "-exec".

---

### Post by blenderfox on 2011-07-30
Thank you :)

---

### Post by AlphaLexman on 2011-07-30
> **momokoyukino said:**
> Just wondered, what does the {} and + mean at the end of the line?
The '**{}**' is explained correctly previously,...

The '**+**' tells the execution command to invoke only once.

In your example, think of many commands...
[LIST]
[*]rename file01.JPG file01.jpg
[*]rename file02.JPG file02.jpg
[*]rename file...JPG file...jpg
[*]and so on, and so on...
[/LIST]
The '**rename**' command is invoked for each file.

With the '**+**' think of it as all one command line, invoking the rename command only once...
[LIST]
[*]rename file01.JPG file01.jpg + file02.JPG file02.jpg + file...JPG file...jpg + etc...
[/LIST]
I don't believe the above syntax is correct, but is just an example!

---

### Post by l-x-l on 2011-07-30
> **AlphaLexman said:**
> Add the 'find' command to the beginning and use the execute command option of 'find'...

```
find . -name "*.JPG" -exec rename 's/\.JPG$/.jpg/' "*.JPG" {} +
```

**EDIT:** beat by nothingspecial


I use the find & rename command often to rename files in my Music collection. I tweak the code above and use:

```
find . -name "*.JPG" -exec rename 's/\.JPG$/.jpg/' '{}' +
```

The last "*.JPG" is removed because it's unnecessary. The "{}" now has single quotes around it because I believe it helps with file names that contain spaces.

---

### Post by AlphaLexman on 2011-07-30
> **l-x-l said:**
> I use the find & rename command often to rename files in my Music collection. I tweak the code above and use:

```
find . -name "*.JPG" -exec rename 's/\.JPG$/.jpg/' '{}' +
```

The last "*.JPG" is removed because it's unnecessary. The "{}" now has single quotes around it because I believe it helps with file names that contain spaces.
Yes, that is better and definitely more efficient. Noted, and Thank you.

---

### Post by blenderfox on 2011-07-31
Thanks to everyone for their help and contributions :)

---

