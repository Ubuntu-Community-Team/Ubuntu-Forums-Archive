---
title: "Scripting - Provide Password IF Prompted"
date: 2009-11-14
forum: General Help
---

### Post by SuperDodge on 2009-11-14
I am writing a simple script to execute some rsync commands.  I am using the following command for the first backup:

echo mypassword | sudo -S rsync -avz --delete --exclude=".*/" /home/sronnie/Music /media/BACKUP


I want to run three consecutive rsync commands and the problem is that sometimes the rsync command takes long enough that the subsequent lines prompt me for my password; however, sometimes if there haven't been a lot of changes it does not.

How would I script an if statement to supply the password only if prompted for it?

Thanks
-RL

---

### Post by diesch on 2009-11-14
You can use *expect* (not installed by default).

---

