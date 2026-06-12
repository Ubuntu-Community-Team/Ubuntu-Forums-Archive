---
title: "Can I edit a sh script to include a su command?"
date: 2011-03-26
forum: General Help
---

### Post by niallabrown on 2011-03-26
I have a sh script to install a printer driver, however when I run it in the terminal it just spits out text at light speed and shuts down.  I can just catch something about no root access. I tried putting a su (sudo I think) into the beginning of the sh file.  It asked for a password when I ran the script again but then said it was not authenticated when I put it in.

Shouldn't this be the same password as my primary user account on Ubuntu?  If I can get the password right will this idea work?  Maybe I am messing something up.  I'm a very very basic user so please keep it simple if possible.

Thanks

---

### Post by Dark_Stang on 2011-03-26
Just run the script from a terminal with sudo in front of it.
```
sudo ./NameOfScript
```

---

