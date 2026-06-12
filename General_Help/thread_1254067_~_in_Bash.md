---
title: "~ in Bash"
date: 2009-08-30
forum: General Help
---

### Post by LzBy1 on 2009-08-30
What is the difference between /location and ~/location?

Basically, what is the purpose of ~ ?

---

### Post by uylug on 2009-08-30
~ points to your home folder

~/something = /home/youruser/something

---

### Post by jrox717 on 2009-08-31
If you'd like to learn more, I've used [this]("http://www.linuxconfig.org/Bash_scripting_Tutorial") website for reference before.

---

### Post by The Cog on 2009-08-31
Like plenty of other command-line input, it is expanded by teh bash command interpreter before being passed to the program being launched, so the program doesn't need to understand all those funny things. Try (for instance):
**echo ~**

---

