---
title: "How can I get rid of this?"
date: 2011-10-06
forum: General Help
---

### Post by Joentokyo on 2011-10-06
I have a Yahoo account and one of the things you can do to protect your account is create a sign up seal. I usually create one each time I log on because my browser deletes all cookies even though it is set to allow one for Yahoo log on.

To make a short story long, when I do this I can upload an image from my computer.  Whenever I do before opening the pictures folder as it used, it opens the desk top and lists the following file; .~lock.jre-6u26-linux-i586.bin#

If I go to the desktop nothing is there. If I do a search, it cannot be found. 

Is this file necessary. If not how can I get rid of it? :confused:

I am running Ubuntu 11.04.

---

### Post by duke.tim on 2011-10-06
It looks like what I believe is a temporary file, of your Java Runtime Enviorment binary.

I'm guessing it is removed after you are done using it.

(I may be wrong though, any second opinions?)

---

### Post by jazzon on 2011-10-07
It is also a hidden file ( starts with a dot ( . ) )  Try using shell and ls -al.

---

### Post by mastablasta on 2011-10-07
> **jazzon said:**
> It is also a hidden file ( starts with a dot ( . ) ) Try using shell and ls -al.
 
 
or crtl-h in nautilus to show it.

---

### Post by Joentokyo on 2011-10-07
Thanks to all for the tips. I finally got it to show and was able to delete it.

---

