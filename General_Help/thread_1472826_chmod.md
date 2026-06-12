---
title: "chmod"
date: 2010-05-04
forum: General Help
---

### Post by amdefeo on 2010-05-04
Hi everyone, 

I need some help with a command. 
I am looking to change the file access for multiple media files in a folder. I want to allow "others" to read and write the files. 
The problem is firefly will not stream the files because the file access wont allow it. 
The folder is located /home/andrew/desktop/music/common music 
this folder has other folders that that house the individual media files. 
I know its a beginner question but how do I use the chmod command in this application? 

Thank You!

---

### Post by SnickerSnack on 2010-05-04
```
cd ~/andrew/desktop/music/common\ music
chmod -R 666 *
```

This will change the permissions for everything in the common music directory and *everything in a every subdirectory*.  If you only store music there, then that's not a problem, it's exactly what you want.

You should also have a look at

```
man chmod
```

It gives all the info you need about the command, but it does take a little while to read the whole thing.  When I need to learn a new use for a commnad, I usually open up the man page and skip down to the section titled OPTIONS.

---

### Post by darolu on 2010-05-04
The problem with "666" permissions it will change the default behaviour of directories as they need 755 to work correctly with some processes (the directories, not their files). I would add write permissions to the files instead (considering that by default all of them can be read by all).
```
$ chmod -R a+w ~/desktop/music/common\ music
```

---

### Post by SnickerSnack on 2010-05-05
> **darolu said:**
> The problem with "666" permissions it will change the default behaviour of directories as they need 755 to work correctly with some processes (the directories, not their files). I would add write permissions to the files instead (considering that by default all of them can be read by all).
```
$ chmod -R a+w ~/desktop/music/common\ music
```

Thanks for the correction.

---

### Post by dino99 on 2010-05-05
the easiest way its using mountmanager

---

### Post by SnickerSnack on 2010-05-08
> **dino99 said:**
> the easiest way its using mountmanager

How would he do that?

I'm eager to so how it would be easier than running a single command. :) (Unless you think that changing file permissions won't work.)

---

