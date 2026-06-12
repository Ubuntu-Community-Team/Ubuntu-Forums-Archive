---
title: "I can't find a folder on Ubuntu 10.11"
date: 2012-03-06
forum: General Help
---

### Post by clausrei on 2012-03-06
Hi,

I try to install a plug in for Gimp and I can not find the folder were it should be saved:  

/home/user/gimp-2.6/plugins   ( This seem to be a directory, which existed on  Ubuntu 10.04 )

But on my computer in directory home is only a folder of the user markus (which is me ). In this directory is NO such thing as a folder user. 

What do I do wrong ?

---

### Post by Hikayu on 2012-03-06
> **clausrei said:**
> Hi,

I try to install a plug in for Gimp and I can not find the folder were it should be saved:  

/home/user/gimp-2.6/plugins   ( This seem to be a directory, which existed on  Ubuntu 10.04 )

But on my computer in directory home is only a folder of the user markus (which is me ). In this directory is NO such thing as a folder user. 

What do I do wrong ?

Ahh, beginner's mistake :3

Don't worry too much, just replace "user" with your user id, "markus".

Btw, we generally call "folders", "directories" here. "Folders" is some crazy name Microsoft/Apple came up with. Either one, just don't use "folder". It's so colloquial it's wrong.

Cheers in advance, Hikayu.

---

### Post by claracc on 2012-03-06
You have plugins folder in a hidden folder: /home/user/.gimp-2.6/plug-ins.

Note the . before gimp-2.6

In nautilus, to see hidden folders you will have to select in see menu, show hidden files.

---

### Post by clausrei on 2012-03-06
> 
Don't worry too much, just replace "user" with your user id, "markus".


What do mean replace , rename it  ? NO 
replace it in the path in a terminal ?

---

### Post by Hikayu on 2012-03-06
> **clausrei said:**
> What do mean replace , rename it  ? NO 
replace it in the path in a terminal ?

No, replace "user" with "markus", so that "/home/user/gimp-2.6/plugins" becomes "/home/markus/gimp-2.6/plugins"

And, ofcourse, taking your post into consideration, making it: "/home/markus/.gimp-2.6/plugins"

Right?

---

### Post by clausrei on 2012-03-06
I got it,   thanks !

---

### Post by claracc on 2012-03-06
As you get solved your problem, please mark the thread as solved using thread tools

---

