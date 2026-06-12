---
title: "Dropbox does not connect automatically."
date: 2010-06-19
forum: General Help
---

### Post by bhishan on 2010-06-19
This is a recent problem, may be about a week. Upon booting my computer, Dropbox does not connect to the internet. I have to stop dropbox from the top panel and run it again from the menu. Then only it connects. Any solutions?

---

### Post by rifak on 2010-06-19
the same thing is happening to me, but it's not every time the computer turns on. it seems to be random whether or not dropbox connects at start-up. it might be a server connection problem on dropbox's side, but i dont know how to confirm that. im waiting for an update from dropbox to see if it fixes the problem before i do anymore investigation.

---

### Post by bhishan on 2010-06-21
> **ego-sum-deus said:**
> the same thing is happening to me, but it's not every time the computer turns on. it seems to be random whether or not dropbox connects at start-up. it might be a server connection problem on dropbox's side, but i dont know how to confirm that. im waiting for an update from dropbox to see if it fixes the problem before i do anymore investigation.

I use XP in my office and Lucid at home. Its just the home computer that has the problem. This happens almost 80% of the time in my home computer.

---

### Post by jakupl on 2010-08-15
I worked around it by [writing this simple bash script]("http://dl.dropbox.com/u/1278270/latliggja/restartdropbox.sh"). Download it, make it executable by right clicking it and going to the permissions tab.
Now go to System -> Preferences -> Startup Applications, click add, name it something and in the command field, write:
```
sh /path/to/file/restartdropbox.sh
```

Now your dropbox should restart 150 seconds after you've logged in, edit at will!

---

### Post by bhishan on 2010-08-16
> **jakupl said:**
> I worked around it by [writing this simple bash script]("http://dl.dropbox.com/u/1278270/latliggja/restartdropbox.sh"). Download it, make it executable by right clicking it and going to the permissions tab.
Now go to System -> Preferences -> Startup Applications, click add, name it something and in the command field, write:
```
sh /path/to/file/restartdropbox.sh
```

Now your dropbox should restart 150 seconds after you've logged in, edit at will!

Thank you

---

