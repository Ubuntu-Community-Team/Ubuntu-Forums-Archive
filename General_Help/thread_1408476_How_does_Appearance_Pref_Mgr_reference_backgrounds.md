---
title: "How does Appearance Pref Mgr reference backgrounds?"
date: 2010-02-16
forum: General Help
---

### Post by Mahngiel on 2010-02-16
Peering into gconf-editor, I noticed that under desktop>gnome>background the picture_filename is the original warty that comes pre-installed on karmic.  
However, I am not using that BG, instead one that i told the Appearance Preference manager to find and use.  Does this app use a symbolic link to refer to the image, or is it elsewhere?  Lookin in /usr/share/backgrounds my image does not exist.
So what is drawing the BG? Is it nautilus or compiz?
And where is the file that tells it so?

Thanks.

---

### Post by Mahngiel on 2010-02-16
Bah. I found it.

~/.gconf/desktop/gnome/background/%gconf.xml

Funny how this displays the correct filepath, but gconf-editor does not.  Anybody know why?

---

### Post by Mahngiel on 2010-02-16
And BTW:  If gnome uses gconf-editor, what does kde use?

---

