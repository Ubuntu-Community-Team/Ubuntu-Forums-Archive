---
title: "Code::Blockes and permissions question"
date: 2009-08-29
forum: General Help
---

### Post by Andyandhisboard on 2009-08-29
Hey guys, I am still new to linux... Im trying to learn how to use it as I run into problems...  Im so confused on permissions stuff.  Like I can't save project files to just about anywhere except desktop (assuming that's a permission thing).  Also, how do you run a program, I just started out with the basic "hello world" console application to get the hang of code blocks on linux (I used dev c++ on windows but cant find it for linux).  Finally I figured out I can save my stuff to the desktop, so I did that.  Then when I ran it, it just showed to location of the file and said Permission is denied or somthing like that.

Thanks,
Andy

---

### Post by Andyandhisboard on 2009-08-30
To the top xD

---

### Post by bear24rw on 2009-08-30
in linux you only have write permission to your home folder (the desktop folder is in your home folder). i use code blocks all the time and personally find it much nicer than dev c++... so you compile you program, did you do a compile a run? if you want to run it on your own go to Accessories > Terminal and type
```
cd Desktop
cd yourprojectfolder/bin/debug
./main

```
obviously changin the name of the directories and executable

good luck

---

