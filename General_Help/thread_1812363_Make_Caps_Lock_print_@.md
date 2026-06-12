---
title: "Make Caps Lock print @"
date: 2011-07-26
forum: General Help
---

### Post by knutschr on 2011-07-26
Is there any way to make Caps Lock print @ instead of the default behavor?

---

### Post by mike555 on 2011-07-26
"Xkeycaps" I think will let you do that , install it from package manager ..... you must run it in terminal ...... sudo xkeycaps  .

---

### Post by knutschr on 2011-07-26
Thank you, it works :-)
Now I must make it work after a restart.

From program's site:
>   The idea is that in the appropriate startup script, you would add a line like
 
                 **xmodmap  /.xmodmap-`uname -n`**
 
in the appropriate init file, so that those keyboard  modifications are made each time you log in.  (If you’re not sure where this command should go, ask your system administrator,  as  that  tends  to vary from site to site.)

Where should I put this line?

---

### Post by knutschr on 2011-07-26
I put it in /etc/rc.local, and now it workes after a restart too

---

### Post by mike555 on 2011-07-26
After setting xkeycaps and then restarting a window should have popped up and asked you to save the setting, you just highlight it and save......

---

### Post by knutschr on 2011-07-26
I did. Chose to save the whole layout. First, I saved only the changes, but then the script didn't work)
Then a massage pop up telling one has to add file to a login script.
At startup before I saved the script, I got a popup as you say, but that did not work.

---

### Post by knutschr on 2011-07-26
Sorry.
May be saving in the popup window, as you said, will work.
I hadn't saved the whole keyboard layout, just the changes, when I tried that.
Thanks again!

---

