---
title: "How do i cut and paste to a root-protected folder?"
date: 2010-11-25
forum: General Help
---

### Post by marcooleo on 2010-11-25
I have some great background wallpapers i have downloaded to my home folder, now i want to place these images in Usr/Share/Background. How do i do that i just cannot cut and paste it there?
Do i have to open up a terminal and login as root? I did that but still not working, or do i have to do all this by terminal-commands?

---

### Post by deserthowler on 2010-11-25
> **marcooleo said:**
> I have some great background wallpapers i have downloaded to my home folder, now i want to place these images in Usr/Share/Background. How do i do that i just cannot cut and paste it there?
Do i have to open up a terminal and login as root? I did that but still not working, or do i have to do all this by terminal-commands?

Get nautilus-gksu from the repository.  It will put an admin selection in the context menu.

Earl

---

### Post by karthick87 on 2010-11-25
Type gksu nautilus in terminal,it will open nautilus with root privileges now you can copy/paste.

```
gksu nautilus
```

---

### Post by s.shawky on 2010-11-25
i had this problem and i found this  solution

To change ownership of a folder, use 

```
sudo chown username:users folder

```
To change ownership of a folder and all of it's contents and subdirectories, use 

```
sudo chown -R username:users folder

```

Replace username with your username, and leave users as is (it is the name of the "users" group).

---

### Post by arpanaut on 2010-11-25
> **s.shawky said:**
> i had this problem and i found this  solution

To change ownership of a folder, use 

```
sudo chown username:users folder

```To change ownership of a folder and all of it's contents and subdirectories, use 

```
sudo chown -R username:users folder

```Replace username with your username, and leave users as is (it is the name of the "users" group).


Please NO!  Not in this case. 

The files and folders the OP wants to paste into are system folders and changing ownership of these can have unforeseen consequences that will affect the operation of the whole system.

Those files and folders must remain with root ownership

Please use the other solutions for non destructive results.

---

### Post by s.shawky on 2010-11-25
so how can i retun the ownership to root

---

### Post by dandnsmith on 2010-11-25
re-run the chown command but with the username and users replaced by the original values (you did make a note, didn't you?)

---

### Post by apollothethird on 2010-11-25
> **s.shawky said:**
> so how can i retun the ownership to root

Tell us where you were when you issued this destructive command.  What is the exact command you issues.  We can look at our default contribution files and tell you what the default attributes are.

In the future, take a lot of concern in making changes to system wide files.

By the way, the command to change owners remains the same.  You'd probably replace the owner root with the owner name you used in the command you issued.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by s.shawky on 2010-11-25
dandnsmith
yes i did
but i can't remember the original value because i am the administrator and the only user

---

### Post by s.shawky on 2010-11-25
> **apollothethird said:**
> Tell us where you were when you issued this destructive command.  What is the exact command you issues.  We can look at our default contribution files and tell you what the default attributes are.

In the future, take a lot of concern in making changes to system wide files.

By the way, the command to change owners remains the same.  You'd probably replace the owner root with the owner name you used in the command you issued.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)
 u can found this topic in the absolute beginner talk 
the topic title  Changing a folder's owner? but i can't remember the link

---

### Post by s.shawky on 2010-11-25
all what i did is changing the ownership of stardict folder to add some dictionaries to it

---

### Post by arpanaut on 2010-11-25
```
sudo chown root:root /path/to/folder
```for the other add the -R for recursive.

Sometimes it isn't a big deal as root can read and write anything but sometimes the system expects certain privileges and that can cause problems.

That's one of the reasons the root user account login is disabled in Ubuntu so people will not unwittingly do damage to the system.  

  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by apollothethird on 2010-11-25
> **s.shawky said:**
> u can found this topic in the absolute beginner talk 
the topic title  Changing a folder's owner? but i can't remember the link

You can find messages on this forum either by:

[INDENT]Click this system's search feature:

[LIST][*]Use text filters with text from the messages of the thread you're looking for.
[*]Search for threads that you've started or typed in.
[/LIST]
You can also put this in a Google Search Bar:
```
site:ubuntuforums.org text filter to find
```
Substitute "text filter to find" with text from the topic you're looking for.
[/INDENT]

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by s.shawky on 2010-11-25
> **arpanaut said:**
> ```
sudo chown root:root /path/to/folder
```for the other add the -R for recursive.

Sometimes it isn't a big deal as root can read and write anything but sometimes the system expects certain privileges and that can cause problems.

That's one of the reasons the root user account login is disabled in Ubuntu so people will not unwittingly do damage to the system.  

  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

thank you i have changed it to root and thank you again fo your warning

---

### Post by marcooleo on 2010-11-25
Thank yo guys for your help, problem solved! :)

---

### Post by apollothethird on 2010-11-25
> **marcooleo said:**
> Thank yo guys for your help, problem solved! :)

Great.  Consider using the "Tread Tools" link to mark it solved.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by yetiman64 on 2010-11-25
> **marcooleo said:**
> Thank yo guys for your help, problem solved! :)

To mark your thread solved, so it shows as solved in the subforum it was posted, check out link #5 in my sig for instructions.

regards
yetiman64

Edit: apollothethird got it first :-)

---

