---
title: "PATH environment variable"
date: 2010-10-20
forum: General Help
---

### Post by mglyons on 2010-10-20
I have just installed Ubuntu onto my machine and my question is if it automatically comes with the PATH environment variable?

If so, how do I add something such as python.exe to the PATH environment variable?

---

### Post by oregonbob on 2010-10-20
Yes, there is a default PATH variable. If you go to a terminal and type "echo $PATH" you can see what it says. Say you want to add /home/bin to your path, that would be command:

PATH=$PATH:/home/bin 
export PATH

You want to add the names of folders containing your executables. Usually when you install packages like python the install script does the path for you.

---

### Post by mglyons on 2010-10-20
Thanks!  Everything works now! :)

---

