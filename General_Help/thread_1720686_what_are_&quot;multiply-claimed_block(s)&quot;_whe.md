---
title: "what are &quot;multiply-claimed block(s)&quot; when running e2fsck?"
date: 2011-04-03
forum: General Help
---

### Post by Naggobot on 2011-04-03
what are "multiply-claimed block(s)" when running e2fsck?

And should I reply yes to question

```
Clone multiply-claimed blocks(s)<y>?
```

---

### Post by Naggobot on 2011-04-04
Bumb

This is related to 

[http://ubuntuforums.org/showthread.php?t=1720375](http://ubuntuforums.org/showthread.php?t=1720375)

which I have now marked as solved but I would appreciate if this could also be closed as Solved.

---

### Post by ronnielsen1 on 2011-04-04
> which I have now marked as solved but I would appreciate if this could also be closed as Solved.
[COLOR="Red"]Thread tools > Mark this thread as solved[/COLOR] in the upper right corner

---

### Post by Naggobot on 2011-04-04
Sorry 

I was unclear. By 

> I would appreciate if this could also be closed as Solved.I meant that we need some solution for this thread also. The original question still remains unanswered

> what are "multiply-claimed block(s)" when running e2fsck?and if an answer to this can be found then this thread can be marked as Solved.

---

### Post by LostFarmer on 2011-04-04
This will be some what a guess and based on my understanding of MS Windows method of file check.

If you have file "A" of 5 blocks "blks 10,11,12,13,14"
                 file "b" of 5 blocks " blks 25,26 27 28,14"
You notice blk 14 is calmed by both files.  You have a choice to delete blk 14 from both files or clone blk 14 to say blk 29 for file "b" =blks 25,26,27,28,29.

The problem should never happen unless there is a bad shutdown.  It is next to impossible to say if blk # 14 should be kept for both files or discarded. If e2fsck would gave both file names it would help , but only urlclassifier3.sqlite is listed.

Rereading your error log , it might be some what different.  It says 7 
multiply-claimed block by one file. likely example:  blocks for file 10,11,12,10,13,10 ect , where blk 10 is listed 7 times. In this case no matter what the file will be bad.  If yes was seleted the blk 10 would be cloned to 6 different blk and the new cloned blk would replace blk 10. Where the file blocks would now be 10,11,12,20,13,21 ect. Blks 20,21 would be the cloned blk 10.

---

### Post by Naggobot on 2011-04-04
Thank you

I think that in this instance an educated guess is much better than total ignorance :P.

As noted in the other thread I replied yes to all prompts by e2fsck and I have now been running error free for about a day.  It is nice to hear that there was no definite correct solution to apply so I can not have made a huge mistake either. 

Marking this thread as solved.

---

