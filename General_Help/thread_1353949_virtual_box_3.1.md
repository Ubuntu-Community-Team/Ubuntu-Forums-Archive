---
title: "virtual box 3.1"
date: 2009-12-13
forum: General Help
---

### Post by odm4286 on 2009-12-13
well I used the deb installer on the website to install the closed source edition. But now I can't figure out how to start it lol theres no icons anywhere in my application menu and it doesn't show up in my software center. Any ideas?

---

### Post by Wardje on 2009-12-13
Open up a terminal, type
```
virtualbox --help
```

If that shows version 3.1, then edit your main menu (see below) and add it manually.

If that doesnt show version 3.1 (in my case: Sun VirtualBox Graphical User Interface 3.0.8_OSE), try typing in "virtua" in your terminal window and then pressing tab twice to bring up all suggestions. If it has another virtualbox entry, try that one out to see if it is your version 3.1.
If it is, add that command to the main menu. If it isnt, assume something has gone wrong (not sure there).


EDIT: Possibly simpler way to check for virtualbox program:
```
ls -1 /usr/bin | grep virtual
```


Adding to main menu:
Right click menu, press "Edit Menus".
Click the category you want the program entry in, then press New Item.

Type: Application
Name: Virtualbox
Command: virtualbox (or if you had to look for a different command, use that one)
Comment: Whatever you want

---

### Post by chriswyatt on 2009-12-13
I find sometimes the Applications menu doesn't update, you could try logging out and logging back in again.

---

### Post by odm4286 on 2009-12-13
hmmm says its not installed weird considering i used the deb package from the website

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by odm4286 on 2009-12-13
ah found it thanks guys

---

### Post by Dennis N on 2009-12-13
After installing, log out and log back in and it will show up under Applications > System Tools.

---

### Post by Wardje on 2009-12-13
> **odm4286 said:**
> ah found it thanks guys

Explain what was wrong/how you had it solved, so others can find the solution in this thread instead of needing to make a similar one ;)

---

### Post by paul_anders on 2009-12-13
another way to find what seams like missing apps by running alacarte in the terminal then look through the menus.

---

### Post by kulambi on 2009-12-14
Hi,

I too faced this problem even after logging out and in again, u can find the executable in /usr/bin/VirtualBox. Just execute this from shell or alternatively you can create a shortcut for this location and you will be able to launch the virtualbox.

Regards,
Sandeep

---

