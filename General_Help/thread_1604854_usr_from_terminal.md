---
title: "usr from terminal"
date: 2010-10-24
forum: General Help
---

### Post by ki4jgt on 2010-10-24
how do you get to the usr directory from command line.

---

### Post by uidb4056 on 2010-10-24
cd /usr

---

### Post by efflandt on 2010-10-24
If you want to add or modify any files in /usr or elsewhere in system directories you usually have to use **sudo** followed by the command.

---

### Post by ki4jgt on 2010-10-24
I did cd /usr then I did a lil Google search and found out why it wasn't working. I had to get to the filesystem directory which was /. I tried Sudo su and only got to roots directory then I cd / and then cd usr and it worked. Thanks guys.

---

### Post by yetiman64 on 2010-10-24
> **ki4jgt said:**
> I did cd /usr then I did a lil Google search and found out why it wasn't working. I had to get to the filesystem directory which was /. I tried Sudo su and only got to roots directory then I cd / and then cd usr and it worked. Thanks guys.

Doing "cd /usr" from the terminal prompt in the home folder here works ok. 

Where you originally typing in "cd usr" from your home directory? It won't work as it only looks in /home/<yourusername> for a folder called usr (which normally doesn't exist). 

However (from your home folder - where the terminal defaults to) putting in the **absolute **path "cd /usr" will work **without** needing to go to a root prompt.

To sum up, cd usr is **not** the same as cd /usr. (uidb4056's post was on the mark)

---

### Post by ki4jgt on 2010-10-25
I was issuing cd /usr but it didn't work either. I've recently dropped the laptop and have been having trouble with it.

---

