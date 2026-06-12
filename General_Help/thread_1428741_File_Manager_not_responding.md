---
title: "File Manager not responding"
date: 2010-03-13
forum: General Help
---

### Post by Steve Francis on 2010-03-13
When I click on a folder under the Places menu or start File Manager, the File Manager window appears and just freezes.

I then have to force quit and receive the error message "File Manager not responding".

When I force quit my desktop items are missing!

GNOME commander works fine. When I type in Nautilus in the command line, no error messages appear.

Is there anyway that I can fix this, please?

---

### Post by Steve Francis on 2010-03-13
Any ideas?

---

### Post by Steve Francis on 2010-03-14
Could someone suggest a link to reinstalling nautilus, please?

---

### Post by Steve Francis on 2010-03-14
I tried reinstalling Nautilus using this code:
    >  Code:
     sudo apt-get remove nautilus
sudo apt-get install nautilus 
This succeeded in uninstalling and reinstalling Nautilus but the File Browser still hangs when I double click on a file within it.

---

### Post by Steve Francis on 2010-03-14
Still working on this problem.

I found out that nautilus does _not_ hang when I type
[FONT=Courier New]gksudo nautilus[/FONT]

If I just type [FONT=Courier New]nautilus[/FONT], I get the error message
[FONT=Courier New]** (nautilus:5550): WARNING **: Unable to add monitor: Not supported[/FONT]
and then I have to force quit the file browser.

I thought maybe I should reset the permissions for my home folder.
Typing the following command did not solve the problem.
[FONT=Courier New]sudo chmod 700 /home/me[/FONT]

This is very frustrating!

---

### Post by Steve Francis on 2010-03-16
Last bump - promise

---

### Post by drinkleadsoup on 2010-03-30
I have the same issue.  Any resolve?

---

### Post by Steve Francis on 2010-03-31
> **drinkleadsoup said:**
> I have the same issue.  Any resolve?

Not yet, unfortunately. I have started a new thread here:

[http://ubuntuforums.org/showthread.php?t=1443521](http://ubuntuforums.org/showthread.php?t=1443521)

---

### Post by Steve Francis on 2012-08-02
This problem is solved. Solution posted on this thread:

[http://ubuntuforums.org/showthread.php?t=1443521](http://ubuntuforums.org/showthread.php?t=1443521)

---

### Post by nothingspecial on 2012-08-02
Old thread.

Closed.

---

