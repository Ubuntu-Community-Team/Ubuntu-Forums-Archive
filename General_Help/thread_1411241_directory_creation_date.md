---
title: "directory creation date?"
date: 2010-02-19
forum: General Help
---

### Post by ryanf4321 on 2010-02-19
i'm trying to make a script that gives one output if a directory in /home is older than one month, and another if the directory is less than one month old. I looked around and saw that the creation date for directories isn't stored, or at least i couldn't find it? How is this possible to do then? Any ideas?

---

### Post by lordskid on 2010-02-19
the creation date would come out by using the -l switch when doing ls

try

ls -al

with a litlle regexp you should be able to extract the date and time a folder was created

---

### Post by ryanf4321 on 2010-02-26
Thanks. ok, i see what you mean and i'm able to cut out the date from the line i need, but how can i compare it to another date. For example, if the creation date is longer than 1 month from the current date, then print something. Otherwise, dont print anything.

---

