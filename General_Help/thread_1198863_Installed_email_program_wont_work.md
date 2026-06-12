---
title: "Installed email program wont work"
date: 2009-06-28
forum: General Help
---

### Post by sldunn05 on 2009-06-28
I am in college and to check my campus email I need a email client called groupwise. I downloaded the client, and since it was an rpm I used alien to convert it to a deb. Once i installed the program it wouldn't run. It was installed with the appropriate extension in the internet folder, but if i click on the icon nothing happens. What can i do to make this work? I though about inserting a sudo command into the icon command but am not sure how to do this. How do i get it to work?

---

### Post by TeoBigusGeekus on 2009-06-28
Open a terminal, type
```
groupwise
```
and post us any error messages.

---

### Post by sldunn05 on 2009-06-28
stuart@stuart-laptop:~$ groupwise
/opt/novell/groupwise/client/bin/groupwise-bin: error while loading shared libraries: libjvm.so: cannot open shared object file: No such file or directory

I have been messing around with it so this probably isnt probably isnt the output of a fresh install. i read elsewhere that the problem could be with the java version groupwise came with so i tried to have it use the version i have but with no luck.

---

### Post by sldunn05 on 2009-06-28
Yeah here si what i get after a fresh install:
stuart@stuart-laptop:~$ groupwise
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

Java is the problem...need to have it use my current version of java

haha now virtualbox isn't working, im assuming because i tried to move the java file...how to i put java in the correct directory to get virtualbox to run?

---

### Post by sldunn05 on 2009-06-30
bump

---

### Post by Cheesehead on 2009-06-30
Evolution is compatible with groupwise.

The default install has two groupwise-compatibility plugins.
Documentation on using evo as a Groupwise client is at [http://library.gnome.org/users/evolution/stable/bv7wcei.html.en](http://library.gnome.org/users/evolution/stable/bv7wcei.html.en)

---

