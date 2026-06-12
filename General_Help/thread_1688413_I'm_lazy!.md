---
title: "I'm lazy!"
date: 2011-02-15
forum: General Help
---

### Post by nmiltner on 2011-02-15
Sorry for my noob post in advance.
Ok so my question is this, I have a script that is called ./Script.sh from within the directory in which that script resides. Is there a way that I can make that script executable from any directory. 
 
To be more clear:
Lets say that the script resides in /my home/test/ I must be in /test to execute it.
Can I somehow be able to execute it from /my home/another test/folder/
 
I was thinking I could make another script and put it somewhere, but I don't even know how to do that. Sorry for my ramblings.
 
I think the new script would go something like this though
 
#!/bin/bash
# I'm too lazy
 
cd /my home/test/
./Script.sh
 
exit
 
Any help would be appreciated

---

### Post by arbitra on 2011-02-15
I placed my script directly into the bin (/usr/bin/ or some such), and removed .sh so that wouldn't be necessary to call it.

You need to adjust the permissions, though.

---

### Post by hawkmage on 2011-02-15
Make a bin directory under you home directory:
```
mkdir ~/bin
```
Move the script into that directory:
```
mv ~/test/Script.sh ~/bin
```

Log off and back on and you should be good to go.  The defailt profile in Ubuntu will add the bin directory under your home directory automatically to your path.  Any executable script you put in that directory will be runnable by you regardless of where you are.

Hopefully you aren't too lazy to type the command I gave you.

---

### Post by nmiltner on 2011-02-15
Thanks for the quick replies.  I'll try it when I get home!
 
No I'm not too laze to type your commands out.  But I can copy and paste them if I decide to be ;).  Thanks again!

---

### Post by Habitual on 2011-02-15
nmiltner:
I commend you for not being "lazy" but for attempting to be prudent.

---

