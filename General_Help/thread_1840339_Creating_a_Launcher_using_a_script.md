---
title: "Creating a Launcher using a script"
date: 2011-09-07
forum: General Help
---

### Post by UnfairBear on 2011-09-07
Hi!

I'm trying to figure out how to use a script to create a launcher in Ubuntu. 

I'm NOT trying to create a launcher to run a script, I've already done that, what I want is to be able to run a script that basically installs a load of components for an application and finally creates a launcher on the desktop for the startup script which will be included in the package.

I tried googling it but I've only been able to find pages on how to make a launcher for a script.

Any ideas? :o

---

### Post by sanderd17 on 2011-09-07
A launcher is just a *.desktop file, and if you look at such files with a text editor, you can just change the values (path to execute, icon ...)

---

### Post by Azdour on 2011-09-07
+1 to what sanderd17 says.

If you want some more in-depth details about .desktop files and their format look here:

[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

Although I am not sure how up to date the documentation is.

---

### Post by UnfairBear on 2011-09-07
>.<

Okay, let me rephrase my question. How can I make and assign a path to a launcher from the command line? ... In retrospect that's probably what I should have googled...

EDIT: Nevermind, I think I figured it out. Thanks!

---

### Post by sanderd17 on 2011-09-07
Since launchers are just text files, you are asking how you can write text to a file?

Well there are is a lot of info on that topic.

---

