---
title: "Super User authorization failed"
date: 2012-03-15
forum: General Help
---

### Post by paulkruger on 2012-03-15
New to linux. Perhaps I am missing something?

**I am trying to implement samba and need to edit the config file to change the workgroup name.**

I can get to the file okay (nano) but cannot save changes, says I am not authorized.  I go back to terminal and enter "su" then my password but it keeps telling me "authorization failed"

I was only asked upon install for one password ( user ) so assumed it would use same for su.  Is there a default super user password I don't know about if you do not enter a separate password on install ( LiveCD )

How do I edit the samba file? :confused:

---

### Post by wildmanne39 on 2012-03-15
How try it with gksudo.
thanks

---

### Post by paulkruger on 2012-03-15
> **wildmanne39 said:**
> How try it with gksudo.
thanks

What is that?

---

### Post by wildmanne39 on 2012-03-15
Hi, that gives you root powers for about 15 minutes so you can do the task you need to do and it is for the gui, if you are just running the command in the terminal then it would just be sudo.
Thanks

---

### Post by paulkruger on 2012-03-15
> **wildmanne39 said:**
> Hi, that gives you root powers for about 15 minutes so you can do the task you need to do and it is for the gui, if you are just running the command in the terminal then it would just be sudo.
Thanks

So what do I do?  Just type the word sudo ?

---

### Post by wildmanne39 on 2012-03-15
Hi, you type gksudo in front of nano instead of su.

I like gedit instead of nano for editing text files.
Thanks

---

