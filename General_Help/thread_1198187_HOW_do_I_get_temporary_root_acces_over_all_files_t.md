---
title: "HOW do I get temporary root acces over all files till reboot?"
date: 2009-06-27
forum: General Help
---

### Post by bobbyallan on 2009-06-27
FOUND THE COMMAND Never mind thanks.

---

### Post by squaregoldfish on 2009-06-27
su is the command you want. You'll need the root password.

This is for the command line, of course. When you're finished, just use exit to return to normal usage.

Steve.

---

### Post by HiImTye on 2009-06-27
or you can 'sudo nautilus'. that's what I do, I hate using the command line to modify files

---

### Post by kilowattradio on 2009-06-27
> **HiImTye said:**
> or you can 'sudo nautilus'. that's what I do, I hate using the command line to modify files

Press ALT + F2
type **gksu nautilus**
then enter the password. You can now have root access to the hard drive. Be careful!  
You can also create a launcher on the desktop and just put 
gksu nautilus 
in the command box and launch it from the desktop. 
:P

---

### Post by HiImTye on 2009-06-27
yeah, but AWN has a built in terminal thinger that pops up and hides when it loses focus so I just 'sudo nautilus'

I only really ever do this when I need to modify files in 'backgrounds' to let them all show up in the list as I don't mess with the built in files much

---

### Post by Hobgoblin on 2009-06-27
> **squaregoldfish said:**
> su is the command you want. You'll need the root password.


use **sudo su** and you don't need the root password.

---

### Post by mhgsys on 2009-06-27
I always use sudo bash in console or terminal to stay root when I want to.

---

