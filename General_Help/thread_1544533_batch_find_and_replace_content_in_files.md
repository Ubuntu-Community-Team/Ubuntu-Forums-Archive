---
title: "batch find and replace content in files"
date: 2010-08-02
forum: General Help
---

### Post by doomsword2001 on 2010-08-02
hello, 

I have a huge html project and has lots of broken links on ubuntu because its case sensitive.

I have 2 types of images Example123.jpg and example123.jpg

The html files sometimes contain href="path_To_Image/Example123.jpg" but the file is example123.jpg (and sometimes the opposite). 

Does anybody know a way to replace all E*.jpg to e*.jpg ???

I have found some scripts/programs but i am not allowed to use * :mad:

---

### Post by prodigy_ on 2010-08-02
If you're not allowed to use scripts, batch processing might be quite tricky.

Perhaps it'll be easier for you to add symlinks? For example, if you have a file named **/project/Example.jpg** and your code references **/project/example.jpg**, the command will be: ```
ln -s /project/Example.jpg /project/example.jpg
```

---

### Post by MasterGamerJK on 2010-08-02
most high level text editors will have this function built in, there is no need for a script

---

### Post by doomsword2001 on 2010-08-02
can't do it 1 by 1 :/ its too much files

---

### Post by prodigy_ on 2010-08-02
Well, you can also install ciopfs: ```
sudo aptitude install ciopfs
``` and use it to make certain directories case-insensitive. Unfortunately there's not much documentation, besides [the developer's webpage](http://www.brain-dump.org/projects/ciopfs/).

---

### Post by doomsword2001 on 2010-08-03
"ciopfs works by translating every path element to lower case before further 				operations take place" 


I have found a software and renamed all the files to lower case allready. The problem is that the html contains A111.jpg instead of a111.jpg AND a.jpg instead of A.jpg. So Converting all to lower case or all uppercase will work for half of the files.

I have discovered that a windows version of firefox with wine works fine. I may have to stick on that.

---

### Post by cavh on 2010-08-03
Suggest asking in the forums for someone to help you in the use of the commands *sed* or *awk*

---

### Post by doomsword2001 on 2010-08-06
ok, thank you, i will give it one more try but i think sed won't let me use *.jpg or whatever. I will post back if i find a solution.

---

