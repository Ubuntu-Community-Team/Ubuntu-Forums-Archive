---
title: "Backup using keep"
date: 2006-06-20
forum: General Help
---

### Post by caldevil on 2006-06-20
I want to use the keep backup utility of KDE in Gnome. How can I make the keep daemon run at start up?

---

### Post by xXx 0wn3d xXx on 2006-06-20
1. Open up a text file and name it somthing like "keep1"

2. Type "#! /bin/bash" --no quotes at the top

3. Press enter so you are on the next line,

4. Type the command to start the daemon. (ex: sudo keep)

5. Put the script in /usr/bin/local

6. In the Gnome sessions box type whatever you named the script.

---

