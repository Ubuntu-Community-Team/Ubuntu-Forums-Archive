---
title: "Files are showing X 's on the upper left, and cannot be copied or executed using Wine"
date: 2011-03-26
forum: General Help
---

### Post by electric/amoeba on 2011-03-26
Basically i know the files are locked. which is slightly aggravating because it took me at least 20 minutes to properly unmount and mount my Starcraft 2 disc, the files would not run from the CD, so I figure copy them to the hard drive as was suggested on the Wine support page for SC2, so I copied them a directory on the hard drive, and all I want to do is right click the files and click Run with Wine, but instead I keep getting Permission Denied, same for copying the files into another folder, Permission Denied.

I need to know the command to change Permission on a file I suppose or is it something else? Help!!!


I was going to just try and gain total root access to my computer but Johnny California explained in [http://ubuntuforums.org/showthread.php?t=1712719&highlight=gaining+root+access](http://ubuntuforums.org/showthread.php?t=1712719&highlight=gaining+root+access) that in the least small areas of local towns could explode and possibly large scale devastation. Didn't know computing could be that danger but WTF is the command man its gotta be so simple someone help!


Here is original post I started from trying to get this game to work, but every other step there is some small problem slowing me down

Starcraft II Wine Tutorial: [http://jeffhoogland.blogspot.com/2010/07/howto-starcraft-2-on-linux-with-wine.html](http://jeffhoogland.blogspot.com/2010/07/howto-starcraft-2-on-linux-with-wine.html)



SOLVED: Learned about the math involved using the chmod command the change permissions triple 7 's all the way HA!

Let's see if I can get this thing to play...

---

### Post by vivek.pandey on 2011-03-26
you need to make use of chmod . which chmod command extension you need can be seen from man chmod

generally it is chmod +x filename

and did you mark the file executable?

---

### Post by electric/amoeba on 2011-03-26
yessir, made er' ececutable, writable, and readable screw it its just my game! but anyways i thought it was really cool about adding the numbers together to create certain permissions, all fancy like, even the few dos commands i knew need to be changed... 

any good links or suggestions to a list of all the basic commands?

---

### Post by vivek.pandey on 2011-03-26
> **electric/amoeba said:**
> 



SOLVED: Learned about the math involved using the chmod command the change permissions triple 7 's all the way HA!

Let's see if I can get this thing to play...

whats this confusion?

---

