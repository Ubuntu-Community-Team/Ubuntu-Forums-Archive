---
title: "Can't install applications!"
date: 2012-09-22
forum: General Help
---

### Post by Manhi40 on 2012-09-22
Ok, this is really bad an I need help!
When I try to install a application on software center, It doesn't work, apt-get doesn't work either. Here is what happens when I try to use apt-get install: [http://imgur.com/a/ehocd]("http://imgur.com/a/ehocd")
I also have one more problem, and that is that I can't open applications from the launcher (pictures Also in link) I'm not sure, but I think the two problems are related...
Thanks in advance!

---

### Post by diesch on 2012-09-22
Looks like the server for your software sources is broken. 

In Software Center go to "Edit" -> "Software Sources" and choose another server  at "Download from" .

---

### Post by Manhi40 on 2012-09-22
That worked!
Thanks, but now I still need to solve the problem with the dash

---

### Post by Manhi40 on 2012-09-22
Never Mind! I solved it, SOLUTION: 
Second to last reply on [this]("http://ubuntuforums.org/showthread.php?t=1911109&page=2") page

---

### Post by sienile on 2012-09-22
Hey! Mark this thread as solved! (Use the "thread tools" menu at the top.)

To make it easier on others looking for the solution to a similar problem, here's the post he's referring to in the above post:

> **creiss said:**
> **SOLVED**

After setting up a VM of my notebook so I could easily revert all changes and after an hour of deleting every single file in my home folder I while continuously restarting the machine I have found the culprit:

```
~/.cache/software-center
```

After deleting this directory and relogging everything worked - even the software center. As to **why** this caused the problem I can only guess.

Thanks for all your help - may this solution help someone else.

-Christian

---

