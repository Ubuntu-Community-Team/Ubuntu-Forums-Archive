---
title: "How to change directory? Not CD?"
date: 2010-07-15
forum: General Help
---

### Post by antdgar on 2010-07-15
I'm in a different type of shell (this is inside "screen"), I guess. It is like this:

```
sh-3.2$ cd /home/user
sh-3.2$ 
```It doesn't change the directory. Any idea how?

---

### Post by nothingspecial on 2010-07-15
GNU screen?

It should work, works for me, have you messed with your screenrc, or maybe you don`t have your PS1 variable set to show the working directory and you have in fact gone where you thought you had......

....or maybe I`m barking up the wrong tree entirely......

Did you check with pwd?

---

### Post by bodhi.zazen on 2010-07-15
> **antdgar said:**
> I'm in a different type of shell (this is inside "screen"), I guess. It is like this:

```
sh-3.2$ cd /home/user
sh-3.2$ 
```It doesn't change the directory. Any idea how?

What do you mean it does not change directories ?

Use pwd

cd
pwd
cd /
pwd

Just because the prompt does not change does not mean the command failed.

---

### Post by antdgar on 2010-07-15
pwd
thanks.

---

### Post by WorMzy on 2010-07-15
pwd just _p_rints the "_w_orking _d_irectory", cd is the command that actually changes the directory you're in.

---

### Post by Shompol on 2010-07-15
> **WorMzy said:**
> pwd just _p_rints the "_w_orking _d_irectory", cd is the command that actually changes the directory you're in.

"directory you're in" = "_w_orking _d_irectory"

$ cd /home/user
$ pwd
/home/user

SUCCESS!!!

---

### Post by blur xc on 2010-07-15
> **Shompol said:**
> "directory you're in" = "_w_orking _d_irectory"

$ cd /home/user
$ pwd
/home/user

SUCCESS!!!

sounds like you need to fine where ther pompt variable is assigned in your whatever it is you are working in, and have it disply your working directory like a proper prompt should.

BM

---

