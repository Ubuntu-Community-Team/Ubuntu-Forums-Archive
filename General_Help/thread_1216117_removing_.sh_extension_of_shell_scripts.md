---
title: "removing .sh extension of shell scripts"
date: 2009-07-17
forum: General Help
---

### Post by StevenEpic on 2009-07-17
when i try to remove the extension by just renaming it, it turns into a text file. 
id like to know how to remove the extension without having it lose its shell script icon.

is this possible?

---

### Post by t4thfavor on 2009-07-17
I don't think its possible since thats how the icons are assigned. 

Just because it has no icon doesn't mean it cant stil be a shell script, it will execute just like any other. I just wanted to point that out in case you didn't know.

---

### Post by StevenEpic on 2009-07-17
the only reason i want to do this is so the file goes along with the rest, and here is a view of a shell script with no extension and my script with the sh extension
[IMG]http://i28.tinypic.com/69qsg4.png[/IMG]

---

### Post by StevenEpic on 2009-07-17
got it!
all i had to do was add```
#!/bin/sh
```
to the top of the file.

---

### Post by L815 on 2009-07-17
Have you tried doing a:
```
mv file.sh file
```

I haven't noticed the actions of a shell icon, but (maybe) as long as the script has some variant of "#!...(sh or bash here)" it should detect it as a script?

---

