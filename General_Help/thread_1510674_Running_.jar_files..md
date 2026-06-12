---
title: "Running .jar files."
date: 2010-06-15
forum: General Help
---

### Post by Mike808 on 2010-06-15
Alright, as far as I know, I use terminal.  

This is what I get when I start terminal:
> michael@michael-laptop:~$ 

What I want to run is on the Desktop of my Laptop.

Title Being - "Rawr.jar"

What do I need to do?  I have Java fulling installed.

---

### Post by webtechquery on 2010-06-15
Hi there..

A little confusion here..

Do you want to run and execute the jar file in Ubuntu ? Or you want to open the jar files, so that you can be able to see the files existing in that jar file ?

---

### Post by mkvnmtr on 2010-06-15
Quite often I right click on the file and choose to open with java runtime. See if that will work for you. It is not elegant but it will work until you get a launcher.

---

### Post by Mike808 on 2010-06-15
> **webtechquery said:**
> Hi there..

A little confusion here..

Do you want to run and execute the jar file in Ubuntu ? Or you want to open the jar files, so that you can be able to see the files existing in that jar file ?

I am sorry, I should have specified, I mean to run and execute the file.

---

### Post by Rhubarb on 2010-06-15
In the terminal, you'll need to run this:
```
cd ~/Desktop
java -jar Rawr.jar
```

Which will then run the java Rawr.jar application for you.

The "cd ~/Desktop" part changes the current working directory to your dekstop, regardless of what directory you're currently in.

The "java -jar Rawr.jar" part tells java to execute the Rawr.jar application.

If for some reason Rawr.jar doesn't run, then you'll have to change the permissions on the file to be executable, which can be done by right clicking on the icon on the desktop, select Properties, select the Permissions tab, and check the "Allow executing file as program" box.

---

### Post by Mike808 on 2010-06-15
Double Post.  Sorry

---

### Post by Mike808 on 2010-06-15
> **Rhubarb said:**
> In the terminal, you'll need to run this:
```
cd ~/Desktop
java -jar Rawr.jar
```

Which will then run the java Rawr.jar application for you.

The "cd ~/Desktop" part changes the current working directory to your dekstop, regardless of what directory you're currently in.

The "java -jar Rawr.jar" part tells java to execute the Rawr.jar application.

If for some reason Rawr.jar doesn't run, then you'll have to change the permissions on the file to be executable, which can be done by right clicking on the icon on the desktop, select Properties, select the Permissions tab, and check the "Allow executing file as program" box.

Solved.  Thanks man.

---

### Post by fragos on 2010-06-15
On the command line "java file.jar".

---

