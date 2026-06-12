---
title: "It's been too long, I forgot how. Help!"
date: 2011-03-10
forum: General Help
---

### Post by dragon1964m on 2011-03-10
After a week, I am down to the last problem I need to fix. It has been three years since I used Linux. I am surprised at how much I had forgotten.

I found a solution (I hope) to my last problem. But, I can't remember how to do what I need to.

Problem: Installing some themes results in an error: This theme will not look as intended because the required GTK + theme engine 'ubuntulooks' is not installed. 

After searching for a while I found this fix: 


Ubuntulooks Engine Installation Instructions

=============================

Step 1.

Copy libubuntulooks.so and libubuntulooks.la to /usr/lib/gtk-2.0/2.*.*/engines as root (substitute "2.*.*" with your version number)



Step 2.

Copy the Human folder to /usr/share/themes/ as root (or to ~/.themes , but it will only be on your account)



Step 3.

Go into your Gnome Theme Prefrences and select Human (or any other Ubuntulooks enabled GTK theme, Human is just included as an example) as your theme under Controls and Window Border. The metacity theme used on Human is a modified version of ClearLooks 2.0 if you wonder, but any other will do too!

Ok, this is where you get to laugh real hard! I downloaded a tar.gz and extracted the files. How do I move the files from my home directory to the root directory as instructed in steps 1 and 2?

---

### Post by WorMzy on 2011-03-10
You can use
```
sudo mv /path/to/file /path/to/destination
```
from a terminal (Applications -> Accessories -> Terminal),

OR

```
gksu nautilus
```
from the run dialog box (Alt+F2), then move the files with drag and drop/cut and paste.

---

