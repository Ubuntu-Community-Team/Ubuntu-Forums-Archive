---
title: "Directory disappeared!"
date: 2011-03-22
forum: General Help
---

### Post by handijk on 2011-03-22
Hello,

Yesterday i checked out a github repository to my homedir, i edited those files with Eclipse, got tired, shut down my PC and got to bed. This morning i woke up, turned my computer and the complete directory is missing, nothing in the trash.

Could anyone help me getting this directory back??

Thanks

---

### Post by An Sanct on 2011-03-22
Welcome to the forums!

Files don't just disappear so try searching for something you know (ie. some specific extension)

In Nautilus, in the menu, select "Go" and "Search for Files". If that has no effect, use a stronger file manager, I use Krusader, its has an *modification time* search option.

---

### Post by handijk on 2011-03-22
Thanks for your reply! I used this forum a lot in the past but never had to post a topic, great knowledge base.

I'm not at home right now so i can't try the search for last modified files, but i tried searching for the directory name on my complete filesystem with no success. I'm using Ubuntu for quite some time now and i have never experienced sirectories disappearing, i was wondering if it could have something to do with the directory being a github repository.

---

### Post by handijk on 2011-03-22
tried to find all .js files modified yesterday using "find" in the console does not return any results from the directory i was working in...
I am totally amazed, i have never seen files disappearing on any kind of OS or device i have worked with, but it looks like it's actually happening.
Frustrating

---

### Post by An Sanct on 2011-03-23
Yes :) again, files don't just vanish.

There has to be a problem with the disk or a setting of git.

I will assume, that the disk is working 100%, since if it isn't, there is no way I can help .

This is the code from the [Ubuntu wiki]("https://help.ubuntu.com/community/find")

```
find $HOME -iname '*.ogg' -atime +30
```
this in short, finds all ogg files accessed in the last 30 days in the $home folder, modify to your needs, maybe to:
```
find $HOME -iname '*.js' -atime +2
```

I only see the catch of '**-noatime**', it wouldn't find any file on my disks (i have -noatime flag set)

Have you enabled "Show hidden files"?

---

