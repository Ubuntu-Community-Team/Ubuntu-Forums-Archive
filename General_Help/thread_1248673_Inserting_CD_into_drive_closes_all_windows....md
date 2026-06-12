---
title: "Inserting CD into drive closes all windows..."
date: 2009-08-24
forum: General Help
---

### Post by Darles on 2009-08-24
Inserting CD into drive closes all windows and removes all icons and content from my desktop.

When i place and audio CD into the CD drive any windows that i have open such as home folder, documents etc all close and I'm unable to open any folders from the menu until i restart. All content from my desktop disappears too and to get it back i have to remove the CD and restart. Strangely enough Firefox stays open and still works fine. All i want to do is use rubyripper to rip the audio from a CD.

I'm running 9.04

---

### Post by Baelus on 2009-08-24
The gui file browser (Nautilus) let's you work with folders and documents, like when you view your home folder. It's also pretty much in charge of what happens on the desktop. For example, when you insert a usb drive or cd, Nautilus pops up the icon on the desktop and opens a window. At least, that's what it's supposed to. :)

Closing all the windows and losing all the desktop icons is, of course, not normal behaviour. I don't know of a direct fix for this, or even what the exact problem is, but here's something that may give you some info on what's going on.

Open Nautilus (e.g. by going to Places -> Home Folder). Click Edit -> Preferences. Click on the last tab called "Media". This tab will let you set what Nautilus does when you insert a cd/dvd/mp3 player etc.

Playing with those settings may help or, hopefully, point you in a good direction.

- B

---

### Post by Darles on 2009-08-24
Thanks for your response B.

I've also tried opening nautilus (Alt + F2) to access files when the desktop disappears but even that doesn't start up. 

I'm really not sure where to start on this. It could be a problem with Brasero and Ubuntu as i found a bug report with a similar problem but at the bottom it states the bug is fixed with an update to Brasero 2.26.1 and yet that is the version i have.

[Bug link]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/335942")

My question now is can i remove Brasero and just use rubyripper instead which is far superior?

---

### Post by Baelus on 2009-08-24
If Brasero is the problem, I'm thinking that nautilus is opening Brasero to handle CDs. But you have the updated version so it shouldn't be causing trouble.

I'm out of ideas. Someone else may be able to nail it down. All I can say is good luck with it.

- B

---

### Post by Darles on 2009-08-25
bump

---

### Post by Darles on 2009-08-27
bump

---

### Post by P4man on 2009-08-27
Does it only happen with audio cd's ? or also data cds?

Have you checked your log files :

system > adminstration > log file viewer

for any hints of whats happening?

---

### Post by Darles on 2009-08-27
Solved.

The problem was brasero so i followed the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=1144003]("http://ubuntuforums.org/showthread.php?t=1144003")

Which removed brasero and installed nautilus cd burner. Many thanks to all who helped or suggested ideas.

Darles

---

