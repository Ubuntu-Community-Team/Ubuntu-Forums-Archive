---
title: "Can't create crontab"
date: 2010-04-15
forum: General Help
---

### Post by Rohan on 2010-04-15
Hi guys,
A couple days ago I noticed cron stopped working and now I can't create a new file using crontab -e. When I hit crontab -e I get the editor but after saving nothing comes up under crontab -l and the file is blank when I reopen it. I don't have a cron.allow or a cron.deny.

Rohan

---

### Post by ajgreeny on 2010-04-15
Very odd!

Which of the choice of three options for editing the text did you choose?  If nano, which is the preferred application, are you sure you used the Ctrl+X to exit and then chose y to save the file?

---

### Post by Rohan on 2010-04-15
> **ajgreeny said:**
> Very odd!

Which of the choice of three options for editing the text did you choose?  If nano, which is the preferred application, are you sure you used the Ctrl+X to exit and then chose y to save the file?

Ok... that is the strangest thing. I usually write out in nano first with "Ctrl-O" then exit with "Ctrl-X" it saves my crontab if I hit "Ctrl-X" then Y. Maybe Ctrl-O is writing to the wrong temp file. 

I think it works now though. So thanks!

---

### Post by ajgreeny on 2010-04-16
It does not matter whether you do things with nano as I did, or the way you did, both should end up with a crontab file just the same.  It is no different to using gedit to write a file, closing gedit and getting the option to save the file, or saving the file and then closing it; both end in the same file being saved.

Whatever it was, I am glad you have it sorted now.

---

### Post by KeyserSoze93 on 2010-04-16
What happens if you run:

```

crontab -l > file

```

Edit the file, and the run:
```

crontab file

```

I usually do this instead of crontab -e, so that I have a copy of my crontab somewhere, in case I need to copy any commands or whatever.

---

