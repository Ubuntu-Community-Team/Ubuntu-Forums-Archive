---
title: "Glib got deleted"
date: 2010-12-31
forum: General Help
---

### Post by arunthakurmanali on 2010-12-31
hi guys,while i was trying to install GTK2.8.i made a mistake and deleted my glib.now the problem is that ubuntu now reaches upto login screen but have no login window to enter my user name & passwd.can anyone tellme how to restore glib.THANKS.please lookat my new thread with title unkown problem

---

### Post by jvc26 on 2010-12-31
Can you move into a different terminal (ctrl+Alt+F1) for example, if so, you can log in there and run sudo apt-get install <packages> and should be able to recover it.

J

---

### Post by arunthakurmanali on 2010-12-31
hi guys,i was trying to install GTK+2.8,but in the process i made a mistake i deleted Glib,now i m not able to login as my login screen shows me no place enter my user name & passwd.all i get is just a login screen with no login box.thanks in advance.

---

### Post by arunthakurmanali on 2010-12-31
I can enter recovery mode which gives me cmd line interface similar to terminal i hope it should work.anyway THANKS A LOT

---

### Post by zpletan on 2010-12-31
Get to a terminal screen - try hitting Ctrl+Alt+F1 from the login screen, or if that doesn't work, boot into recovery mode.
Make sure you have an Internet connection (ping [www.google.com]("http://www.google.com") and I can't help if you can't get Internet - I only know how to network from a GUI :) ).
sudo apt-get install libglib2.0-0

---

### Post by howefield on 2010-12-31
Threads merged.

---

### Post by arunthakurmanali on 2011-01-01
hi jvc,i tried the technique u suggested but found that i already have glib installed.is there any cmd to check what package is mising.

---

### Post by arunthakurmanali on 2011-01-01
how am i merging thread.kindly tell me difference between tread and posts,how ti reply to threads.

---

### Post by Elfy on 2011-01-01
> **arunthakurmanali said:**
> how am i merging thread.kindly tell me difference between tread and posts,how ti reply to threads.

You can;t merge threads. Staff do that.

Two ways to answer a thread - New Reply button at top of thread and the quick reply button in each post - looks like an Enter symbol

Thread is the whole list of posts - post is each thing written.

Also, please do not post duplicates - you can find your threads and posts from the Search dropdown at the top.

---

### Post by arunthakurmanali on 2011-01-01
thanks alot FORESTPISKIE,it would be very kind of u if u go to my thread with title (unknown problem),i am facing a problem and have no clue of my problem.

---

### Post by zpletan on 2011-01-01
> **arunthakurmanali said:**
> hi jvc,i tried the technique u suggested but found that i already have glib installed.is there any cmd to check what package is mising.
Try sudo apt-get install --reinstall libglib2.0-0

---

