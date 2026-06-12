---
title: "Shell Scripts"
date: 2006-05-31
forum: General Help
---

### Post by AaronThorpe on 2006-05-31
I apologize in advance for being an extreme n00b but here it is. 
I just installed Linux, Kubuntu 5, after being a die hard windows fan for years. (FREEEEDDOOOMMMM!!!!!!!) However, I'm trying to get my wireless card working...boom, thx to these forums got it up and running.
Tried to a deb file installed....failed...and boom, thx to these forums....got it!
Now,  I'm trying to make my life easier by writing a shell script to automatically get my wireless card on my network...Boom thx to these forums, got the script and know how to run it.....but I can't save it.
I used the 

touch "NetworkName"

edited the file in the /usr/local/bin/ directory.....but I can't save it (grrrrrr)

So I did a search on why I couldn't save it....found my username wasn't on the admin list....so I added my user name to the root group using the 

sudo adduser infectionzero root

which returned  user added....

I still can't save to the darn file.....
ok ok fine, I'll just save a DIFFERENT file name....."Hey jerk, you must not get it, you CAN"T WRITE TO THIS DIRECTORY" ....needless to say I'm frustrated....and on top of that, I'm using Kate text editor (go ahead laugh, i already am pretty sure I can't make scripts in that beast of an editor) sooo.....please either respond or just hack into my computer and make it start smoking....either one would fix my problem....Thx

---

### Post by tonyr on 2006-05-31
If you are using **kate**, you need to start it from the command line
(in a terminal) using **sudo**, i.e. **sudo kate**.

---

### Post by IYY on 2006-05-31
Just because you're in the admin group does not mean you are root. To edit a file in the command line:

**sudo** nano filename

---

### Post by tonyr on 2006-05-31
I think, also, that you have some confusion about being on the **admin** list.  The fact
that you can do anything at all with **sudo** means that you **are** on
the **admin** list

---

