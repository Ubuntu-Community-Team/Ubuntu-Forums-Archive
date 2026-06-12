---
title: "General Advice on &quot;To Do List&quot; text Doc Program"
date: 2012-08-08
forum: General Help
---

### Post by Alcidious on 2012-08-08
I have a general advice question to ask; I assumed General Help is the appropriate place to post, as I am not looking for extremely detailed programming... Running Ubuntu 12.04 on a Samsung laptop, 32-bit.  

I want to create a program, possibly C++, that saves each day's to do list ( a simple .txt labeled with day's date, created in a notepad), updates the completed and new tasks to a final list, and shares that list (and updates similar files on different devices, respectively). I want this program to run mainly on my Android Smart phone, but when plugged into my laptop or PC I want the updates and saves to occur.  

I.E. - I create a 8_8_12 .txt file to list my to do's for the day.  I complete some tasks, such as paying bills or meetings with people, which I do not want saved in my general working To Do list. I do want uncompleted tasks to show up on my 8_9_12 file, though  Additionally, I want the earlier and completed tasks stored somewhere in memory, so that I can go back in the future and see what I did.  

When I hook up my Smartphone to my laptop or PC I want the program to run and send copies of the current and saved To Do lists to specific folders on my Linux machines.  I want to have the same, synchronized To Do lists on all my machines (consisting of an Android Thunderbolt and two PC's running Ubuntu 12.04).  I am considering using some form of Remote Desktop client to do the updating and sharing...

My Question is:  I believe I can write a C++ program to save the old files and create new ones, and to perform the update/save routines.  However, should I use Linux Shell Scripts to automate the updating and saving?  I thought maybe use "cat 8_7_12 general_ToDo" to perform the string update/search.  Would this work? What resources could I look into? Any ideas appreciated!
Should I post in another forum that is specific to projects? Sorry for length!

Alcidious

---

### Post by Vaphell on 2012-08-08
i'd use shell, grep, sed, awk, redirection for everything and rsync to sync data.

---

### Post by cortman on 2012-08-08
Sounds like a fun and useful project- someday I want to write a similar program that emulates Microsft OneNote functionality, but utilizes text documents and a clear, easily navigable file structure.
Good luck!

---

### Post by Alcidious on 2012-08-09
Thanks Vaphell, I will look in to that.  Im just glad to know that shell programming can do what I am looking for...I will probably posting again once I run into some actual issues!

---

### Post by Vaphell on 2012-08-09
of course it can, it may not be blazing fast, but offers tons and tons of convenient tools.
Another choice would be python which also comes with an extensive library of toys.

If you post more detail how you imagine this program should work, what the data format should look like, we could provide advice and point you toward solutions.

---

