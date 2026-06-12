---
title: "&quot;Desktop1&quot; folder in home directory"
date: 2009-08-06
forum: General Help
---

### Post by Magical Tiger on 2009-08-06
So far to me, it seems like random times but a folder titled "Desktop1" sans quotes is made in my home directory without anything in it. Does any one know why and how I can stop it? Thanks

---

### Post by esalnoj on 2009-08-06
Not sure, but this may help diagnosis:

Try running "top" without qoutes in terminal the full time your system is running. Leave your home directory open at same time. 

Then, when "Desktop1" is created, see if any out of place processes are running. Post the name of this process back here.

---

### Post by Magical Tiger on 2009-08-08
I have figured out when it happens. I have replaced the "Documents", "Music", "Pictures" ,and "Video" folders with links and whenever I use a link off the "Places" menu the "Desktop1" folder is created.

---

### Post by harry2006 on 2009-08-08
nice catch!!!

---

### Post by esalnoj on 2009-08-11
Sounds like nautilus wants to use "Desktop1" instead of "Desktop".

Try moving and renaming to the folder nautilus wants to use.

---

### Post by Magical Tiger on 2009-08-12
This is nothing to do with desktop "environments" but rather some issue in Nautilus.

---

### Post by Magical Tiger on 2009-08-12
I have managed to fix the problem by moving everything from my "Desktop" folder to the "Desktop1" folder and then deleting "Desktop" and renaming "Desktop1" to "Desktop".

---

