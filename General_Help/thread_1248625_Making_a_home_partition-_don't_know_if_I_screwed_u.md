---
title: "Making a /home partition- don't know if I screwed up?"
date: 2009-08-24
forum: General Help
---

### Post by blur xc on 2009-08-24
I read this tutorial a while ago, [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) and proceeded to move my home folders over to my new partition.  The thing is, I did the steps from memory rather than going step by step through the tutorial.

So- I missed this part-
```
find . -depth -print0 | cpio --null --sparse -pvd /new/
```

Instead I did-
```
sudo cp -R /old/home/* /new
``` 
...after mounting the old partition in /old and the new home partition in /new (according to the tutorial)

Afterwards, I found out that all the files now belonged to root, and group root.
So I did a -
```
sudo chown -R username.username username
```
for the two users' home folders.  Now I could boot and log in normally.

Am I going to run into recurring problems?  So far, after a day, it *seems *as though all is working properly.

I assume the line in the tutorial copies everything over w/o altering file ownerships or permissions.  I personally wish that in every tutorial, instead of having people blindly copy and paste each line into the terminal, they would explain what that line did and why.  That would go a lot further to helping people understand what they are doing.

BM

---

### Post by gldearman on 2009-08-24
I'm not personally seeing any problems here that you don't already know about.  Of course, you'll notice that the last time modified for every file is now no earlier than the date you did the copy.  You probably should have done 

```
sudo cp -pR /old/home/* /new
```

-p preserves existing ownerships, permissions, and timestamps.

But, of course, it's too late now.

If it's any consolation, I also screwed up every one of my timestamps following that same tutorial.

---

