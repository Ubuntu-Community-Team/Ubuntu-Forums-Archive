---
title: "(basic) how to use/read a manual for a code"
date: 2009-08-07
forum: General Help
---

### Post by rhythmiccycle on 2009-08-07
i want to learn how to use 'chmod' and 'chown' to change permissions of folders.

but rather than just having someone tell me what code to type, i want to know how to figure out what to type by reading the manual. i know that i can enter:

man chmod
and
man chown

but when i read the output of "man chmod"  i have no idea how to apply any of that stuff to do what i want.

i've read a couple of tutorials one using the terminal in ubuntu, but but they mainly just explain how to use "cd" "ls" "cp" "rm" "gedit" "nano". and i know that stuff. I want to take my code skills to the next level. 

how does someone learn how to understand how to read a manual, specifically the manual for "chmod" and "chown"?

---

### Post by michy99 on 2009-08-07
The man pages can sometimes be difficult to understand. I suggest using google to find a tutorial instead. This one looks good:

[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---

### Post by rhythmiccycle on 2009-08-07
thanks alot, that showed me what i needed

used the code:

```
 sudo chmod a=rwx /var/www
```
to change the folder.

and

```
 sudo chmod a=rwx /var/www/index.html
```
to change to file in the folder.

thanks!

---

### Post by nikhilbhardwaj on 2009-08-07
its pretty easy to read the manuals

just type man name Of command
in your case
man chmod

and remember you must press q to come out of the manual

---

### Post by michy99 on 2009-08-07
> **nikhilbhardwaj said:**
> its pretty easy to read the manuals

just type man name Of command
in your case
man chmod

and remember you must press q to come out of the manual

Yes, it's easy to read them; understanding them is another matter. Some are more clear than others.

---

### Post by nikhilbhardwaj on 2009-08-07
> **michy99 said:**
> Yes, it's easy to read them; understanding them is another matter. Some are more clear than others.

i'll have to aggree with you on that

---

