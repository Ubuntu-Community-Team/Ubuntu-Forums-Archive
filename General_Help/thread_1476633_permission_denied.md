---
title: "permission denied"
date: 2010-05-08
forum: General Help
---

### Post by MughalShahzad on 2010-05-08
How can I grant permissions to myself to save/edit/delete/execute files from /var/www/.
when I try to save code written in Bluefish 2.0.0 in that location system gives message Could not save file permission denied.

while when I write code in gedit text editor opened from terminal it allows me to save and open the php/html file in browser.

How to come out of this problem please guide me

Thanks & Regards
Shahzad

---

### Post by djchandler on 2010-05-08
> **MughalShahzad said:**
> How can I grant permissions to myself to save/edit/delete/execute files from /var/www/.
when I try to save code written in Bluefish 2.0.0 in that location system gives message Could not save file permission denied.

while when I write code in gedit text editor opened from terminal it allows me to save and open the php/html file in browser.

How to come out of this problem please guide me

Thanks & Regards
Shahzad

You need to change the permissions on that directory to write directly to it, but that is probably not a good idea.

Save your code in your home folder. Then use the terminal to copy it as super user (sudo cp filename /var/www) to the directory /var/www.

Surely there must be instructions to set your programming environment so this can be less trouble.

Did you search for "bluefish" in the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") forum? You need to "dig" to find that forum. You may want to post your question there.
[URL="http://ubuntuforums.org/forumdisplay.php?f=39"]
Ubuntu Forums  > The Ubuntu Forum Community  > Other Community Discussions  > Development & Programming > Programming Talk[/URL]

Good luck!
:D

---

### Post by MughalShahzad on 2010-05-08
Thank you soooooo much :p

Regards
Shahzad


> **djchandler said:**
> You need to change the permissions on that directory to write directly to it, but that is probably not a good idea.

Save your code in your home folder. Then use the terminal to copy it as super user (sudo cp filename /var/www) to the directory /var/www.

Surely there must be instructions to set your programming environment so this can be less trouble.

Did you search for "bluefish" in the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") forum? You need to "dig" to find that forum. You may want to post your question there.
[URL="http://ubuntuforums.org/forumdisplay.php?f=39"]
Ubuntu Forums  > The Ubuntu Forum Community  > Other Community Discussions  > Development & Programming > Programming Talk[/URL]

Good luck!
:D

---

