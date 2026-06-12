---
title: "help with deleting/editing path variable"
date: 2010-02-28
forum: General Help
---

### Post by honey toast on 2010-02-28
Hi ,

I am in the middle of manually installing the latest jdk and jre onto my laptop which is running 9.10. 
I am following the tutorial found here:[HTML]http://ubuntuforums.org/showthread.php?t=1113039[/HTML]

I am currently at the part of the tutorial where it shows how to set the variables up for a single user, or  [B][U][SIZE=2]5.2 Settings the variables up for a single user

[/SIZE][/U][/B][SIZE=2]So basically, I am seeking help right now because I made a mistake when setting my path below:

[/SIZE]```

echo "export JAVA_HOME=/usr/local/<JAVA_FOLDER>/bin/java" >> $HOME/.profile
```

Now, I would like for someone to explain to me how to edit this path or delete it all together so that I can start over.
In the tutorial, the author explains how to delete an incorrect path like this:

**If you accidentally added an incorrect PATH variable open your home folder, press ctrl.h and remove the offending lines (at the bottom of the file) using a text editor.**

Except when I tried to hold down ctrl.h in my home dir, nothing appeared to happen that would reveal a list or something so that I could delete the old path and make a new one. Am I looking for a list of some kind? I can sure use some help with this. 

If I were to just set a new path with ...
```

echo "export JAVA_HOME=/usr/local/<JAVA_FOLDER>/bin/java" >> $HOME/.profile 
```
would it overwrite the old one and solve my problem? Thanks for your input.

---

### Post by geirha on 2010-02-28
> **honey toast said:**
> 
If I were to just set a new path with ...
```

echo "export JAVA_HOME=/usr/local/<JAVA_FOLDER>/bin/java" >> $HOME/.profile 
```
would it overwrite the old one and solve my problem? Thanks for your input.


That command will append the line «export JAVA_HOME=/usr/local/<JAVA_FOLDER>/bin/java» to the end of $HOME/.profile. Running it twice will leave you with two identical lines.

To edit the file manually, you can run (in a terminal) ```
gedit "$HOME/.profile"
```

Files starting with ., like .profile, are hidden by default. Hitting Ctrl+H in nautilus should toggle showing hidden files or not. Once hidden files are shown, you can double click .profile to edit it.

---

### Post by honey toast on 2010-02-28
Ok- that does make sense. So if I were to run this again...

```

echo "export JAVA_HOME=/usr/local/<JAVA_FOLDER>/bin/java" >> $HOME/.profile

```

but only different from the first config, then the second setting would overwrite the first one, if they were different? You're saying the second will just append the first?.... I think I got it now. Thanks!

---

### Post by honey toast on 2010-02-28
Ok- that does make sense. So if I were to run this again...

 	Code:
 	echo "export JAVA_HOME=/usr/local/<JAVA_FOLDER>/bin/java" >> $HOME/.profile 
but only different from the first config, then the second setting  would overwrite the first one, if they were different? You're saying the  second will just append the first?.... I think I got it now. Thanks!

---

### Post by geirha on 2010-02-28
> **honey toast said:**
> Ok- that does make sense. So if I were to run this again...

 	Code:
 	echo "export JAVA_HOME=/usr/local/<JAVA_FOLDER>/bin/java" >> $HOME/.profile 
but only different from the first config, then the second setting  would overwrite the first one, if they were different?

Well, yeah, if you add two lines that both assign some string to the environment variable JAVA_HOME, then both will be run when .profile gets sourced, but the last assignment will overwrite the first.

You should just edit .profile manually and make sure there's only one line at the bottom that sets JAVA_HOME

```
export JAVA_HOME=/usr/local/<JAVA_FOLDER>/bin/java
```

---

