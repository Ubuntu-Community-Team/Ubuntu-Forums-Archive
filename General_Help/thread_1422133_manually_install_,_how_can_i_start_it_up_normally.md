---
title: "manually install , how can i start it up normally?"
date: 2010-03-05
forum: General Help
---

### Post by honey toast on 2010-03-05
I just installed eclipse 3.5 manually from the eclipse website and installed it into my /opt directory. I do not see where I can make an executable icon for this, so will someone please give me some direction or post a link. THanks.

---

### Post by darolu on 2010-03-05
The easiest way is to create a symbolic link in one of the directories in your $PATH.

To learn what directories are in your $PATH, open a terminal and execute this:
```
$ echo $PATH
```
You can create the symbolic link within any of this folders, symbolic links for this kind of apps (inside /opt) are usually made inside /usr/bin:
```
$ cd /usr/bin
$ sudo ln -s /opt/eclipse/./eclipse eclipse
```
This way you can run eclipse by typing "eclipse" in your terminal or ALT+F2 or with a launcher.
Just make sure to create the symbolic link to the actual program, my route is just an example :p

Remember, your eclipse binary file must have execution permissions.

---

### Post by honey toast on 2010-03-05
thanks a bunch. it worked fine.:D

---

