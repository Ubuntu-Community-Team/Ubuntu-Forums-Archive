---
title: "how do I run a  &quot;.jar&quot; file at start up (specifically remoteDroid)"
date: 2011-12-23
forum: General Help
---

### Post by rhythmiccycle on 2011-12-23
I use remoteDroid to use my phone as a wireless mouse.
the ".jar" file was downloaded from here:[http://remotedroid.net/]("http://remotedroid.net/")

the file works fine when i double click on it manually.(i.e. double click on the jar icon after the os is loaded)

The problem I'm having is making it load at start up.
I also tried dragging the file into the top panel (a spring board icon  shows up), and that doesn't work either. When I click on the panel icon,  the "jar" doesn't open.  

I first tried adding the file to "startup applications" via "preferences", but it is not opening at start up.

I currently have the jar file on the desktop, and open it after the os loads.

when the file is clicked on, a window pops up, and then the phone can be used as a remote mouse.

it works, but not at start up. Why?

is there a way make this program, and its popup window, open at start up without having to click on it.

---

### Post by Bonster on 2011-12-23
To launch it from the command line is usually

> java -jar /path/to/filename.jar

---

