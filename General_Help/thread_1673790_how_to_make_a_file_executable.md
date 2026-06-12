---
title: "how to make a file executable"
date: 2011-01-22
forum: General Help
---

### Post by snny on 2011-01-22
I use wine to execute my games. Now it says all the exes are unexecutable.I'm not very use to ubuntu and would very much appreciate any help. thanks

---

### Post by kanishkdudeja on 2011-01-22
right click on the file.  select properties. go to permissions tab. and mark the option named "Allow executing file as program".

---

### Post by switch10 on 2011-01-22
There are many ways, here is one.

```
chmod u+x filename
```

---

### Post by damispyderbyte on 2011-01-22
If the exe is on a CD, you cannot change the permissions. 
You have to:

```
wine "program path" 
```

In the terminal

---

### Post by snny on 2011-01-23
I didn't have that option there.

---

### Post by snny on 2011-01-23
right click on the file.  select properties. go to permissions tab. and mark the option named "Allow executing file as program". I don't have this option ...and it isn't on a cd... the code (chmog u+x) I read about but I don't know where to apply it.

---

### Post by ExileAmongYou on 2011-01-23
You also need to right click on the exe, go to "Open with", and choose Wine Program Loader as the default.

---

### Post by snny on 2011-01-23
still won't let it 
I haven't had problems before ..should I reinstall wine?

---

### Post by hakermania on 2011-01-23
> **snny said:**
> right click on the file.  select properties. go to permissions tab. and mark the option named "Allow executing file as program". I don't have this option ...and it isn't on a cd... the code (chmog u+x) I read about but I don't know where to apply it.
Can  you upload a screenshot? Because all files have this option dude!

---

### Post by snny on 2011-01-23
Hope this worked

---

### Post by snny on 2011-01-23
The only options I have are....None, Write only, Read only, Read Write...

---

### Post by snny on 2011-01-23
Thanks you guys for the help. I figured it out. I changed to a command to open file with 'Wine' and it worked..I appreciate your help. Snny

---

### Post by Spyderkid on 2011-01-23
In futur if you ever want to install stuff from cd's just so this its easyier in my opinion.

cd /media/NAME OF DISK
wine setup.exe

---

