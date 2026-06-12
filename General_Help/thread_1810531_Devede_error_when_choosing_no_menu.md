---
title: "Devede error when choosing no menu?"
date: 2011-07-23
forum: General Help
---

### Post by autonym on 2011-07-23
I get an error when trying to convert a .avi file to a .iso file using  Devede. If I leave the "Create a menu with the titles" option as is I  get no error. But I don't want any slideshow so I untick that option. I  then get this error when the process is almost done;  

*Failed to create the DVD tree*
*Maybe you ran out of disk space*

I do have enough disk space so that can't be the problem. Anyone know what to do about this problem?

---

### Post by thefasterblueone on 2011-07-23
Try clicking on "Adjust disk usage" button before clicking "Forward".

---

### Post by autonym on 2011-07-23
Update; I tried adjusting the disc usage before starting the conversion this time. Unfortunately though I got the same error message as before. Any more ideas?

---

### Post by ron999 on 2011-07-23
> **autonym said:**
>  Any more ideas?
You are not alone. :o
Look :- [http://ubuntuforums.org/search.php?searchid=82137258]("http://ubuntuforums.org/search.php?searchid=82137258")

---

### Post by autonym on 2011-07-23
Oyeah!

There is a solution to this problem and that solution is on this page [http://groups.google.com/group/devede-forum/browse_thread/thread/383b147681fc4948](http://groups.google.com/group/devede-forum/browse_thread/thread/383b147681fc4948)

>  For some reason dvdauthor now requires that you export a VIDEO_FORMAT 
 variable, like "export VIDEO_FORMAT=PAL". 
 
So I ran: 
 
# export VIDEO_FORMAT=PAL 
 # devede 
 
And now we have another mistery revealed... ;) 

I'm marking this as solved!

---

