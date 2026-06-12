---
title: "Changing folders in the terminal"
date: 2009-09-11
forum: General Help
---

### Post by DarkPanther on 2009-09-11
Hello, I'm having a problem changing folders in the terminal. When I try to change folders it says it doesn't exsist, of course it does :) Any help on me being able to change folders to the desktop is greatly appreciated.

Here's a screen shot. 
[IMG]http://i27.tinypic.com/2yo1vgp.jpg[/IMG]

---

### Post by staf0048 on 2009-09-11
Hmmm - is the folder "wes" capitalized?  Such as "Wes" or "WES"?

Sorry, just realized something.  Try changing directories without the / before wes and see if that works.

---

### Post by akakingess on 2009-09-11
Yes, it may help if you could do an "ls" while in the home folder so that we could see for a fact that it is in there and the capitalization, etc. (not trying to be nosy, and completely understand if you don't want to do that, just a suggestion).

---

### Post by Efwis on 2009-09-11
you need to have the full structure there to change directories

```
cd /home/wes
```

also why are you doing it from root? you should be able to go there without being in root

---

### Post by Snowman314 on 2009-09-11
Don't forget that the command cd /wes is different from cd wes. The first looks for a folder called 'wes' in the root folder, the second looks for a folder called 'wes' in the current folder.

---

### Post by kaibob on 2009-09-11
I think you need to type "cd wes" rather than "cd /wes".

---

### Post by Shujah on 2009-09-11
Yes, cd /wes means an absolute path to /(root) /folder wes. You have to try it like 'cd wes' (relative path) or 'cd ~/wes' (absolute).

(By the way '~' in address ought to make the second command semi relative too..)

---

