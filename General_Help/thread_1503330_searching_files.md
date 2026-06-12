---
title: "searching files"
date: 2010-06-06
forum: General Help
---

### Post by pko76 on 2010-06-06
hello i want to find files for example that start with p in the current directory and all subdirectories.also i want to change the permission of them. i use ls -lh * | grep "p*" but it does not give the right results.i want only the files that start with p.thank you

---

### Post by Smart Viking on 2010-06-06
Hey, try this:

find / | grep "p" | less

Where "/" is the directory you are searching in. :)

EDIT: Ups no, that command wont do it lol. I'll try some more haha

EDIT2: No actually, that command does do it i was wrong! xD

---

### Post by unix_user on 2010-06-06
Try this command by specifying to start in current directory and all its subdirectories 

find . -type f -name 'p*' -exec chmod 0755 {} \;

another approach:
find . type f -name 'p*' | xargs chown 0755

Hope this helps, specify as permissions as needed, 0755 is shown as example.

Thanks,

---

