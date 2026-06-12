---
title: "Python and installers...in windows."
date: 2010-01-16
forum: General Help
---

### Post by Hunter2379 on 2010-01-16
Let's say you installing firefox. It asks you for next, then the accept agreement, then next, etc.
I wanna make a script in python that will automate this. You run the script and it will automatically install firefox. 
I then wanna incorporate that into a script that installs firefox, then java, then flash, then a few other programs into window. 
Like one script installs all.

---

### Post by Cheesemill on 2010-01-16
This has already been done. Check out [Ninite]("http://ninite.com/").

---

### Post by n0dix on 2010-01-16
> **Cheesemill said:**
> This has already been done. Check out [Ninite]("http://ninite.com/").

Did not know about this program. Only run in Window$:(

---

### Post by Cheesemill on 2010-01-16
The OP asked about Windows.

Also there is no need for a program like this in Ubuntu when you can just do:
```
sudo apt-get install vlc sun-java6-jre flashplugin-installer .......
```

---

### Post by Hunter2379 on 2010-01-16
wow cool. The whole point though is that i want to write something like it in python.

---

### Post by Cheesemill on 2010-01-16
Sorry, I don't know python.

A place to start is to find out if the installers you want to use have silent install options.

For Firefox first you need to extract the "Firefox Setup 3.5.7.exe" into a temporary folder, then run "setup.exe -ms". The -ms switches force a silent install.

---

### Post by Hunter2379 on 2010-01-16
Is there anyone here that can help me with this?

---

