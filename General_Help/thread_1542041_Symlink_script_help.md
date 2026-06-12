---
title: "Symlink script help"
date: 2010-07-30
forum: General Help
---

### Post by Kerbeh on 2010-07-30
My movie collection has spread over multiple drives and I want to  accses them from the one directory, all my movies have there own  directorys but are spread over a few drives

Is it possible to make a symlink to link the contents of /mnt/movies to  /home/movies rather than just making a shortcut of /mnt/movies within  /home/movies

Or will I have to make a script that symlinks all the subdirectories of  /mnt/movies to /home/movies. If so how would I go about it, both writing  the script and where/when would it be executed?

Running 10.04 btw

---

### Post by DaithiF on 2010-07-30
Hi,
not totally sure I've understood you correctly, but:
```
rm -f /home/movies
ln -s /mnt/movies /home/movies

```
will delete the directory /home/movies, and replace it with a symlink to /mnt/movies

---

### Post by ad_267 on 2010-07-30
> **DaithiF said:**
> Hi,
not totally sure I've understood you correctly, but:
```
rm -f /home/movies
ln -s /mnt/movies /home/movies

```
will delete the directory /home/movies, and replace it with a symlink to /mnt/movies

I think the problem is that there is /mnt/movies1, /mnt/movies2 etc.

So OP wants all of the contents from each drive to show up in /home/movies. Eg:
```
ls /mnt/movies1:
movie1
movie2

ls /mnt/movies2:
movie3
movie4

ls /home/movies:
movie1
movie2
movie3
movie4
```

I don't know of a way to do this other than a script to create a whole bunch of symbolic links, and then that would have to be run as a cron job or every time a new movie is added. There are probably a lot more complex ways like making a virtual file system or something.

It would be nice to have a simple way to do this though.

---

### Post by ad_267 on 2010-07-30
Here's what I've found:

[http://ubuntuforums.org/showthread.php?t=558194](http://ubuntuforums.org/showthread.php?t=558194)
[http://www.linuxforums.org/forum/linux-newbie/125391-combine-contents-multiple-folders-into-one-how.html](http://www.linuxforums.org/forum/linux-newbie/125391-combine-contents-multiple-folders-into-one-how.html)

It sounds like UnionFS is what you're after. I haven't used it so don't know how complicated it is to set up though.

---

### Post by worksofcraft on 2010-07-30
lndir /mnt/movie*

should create in your current directory a "shadow tree" of symbolic links to all the files in all the folders that match the name /mnt/movie* . That might help.

edit: no sorry, it doesn't like the *, you would need:
for d in /mnt/movie*; do lndir $d; done

---

