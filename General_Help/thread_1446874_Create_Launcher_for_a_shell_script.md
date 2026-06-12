---
title: "Create Launcher for a shell script?"
date: 2010-04-04
forum: General Help
---

### Post by jacrider on 2010-04-04
After friends experienced a huge loss in a house fire, I decided to try and find a home inventory application.  I found one called "Attic Manager" that works in Ubuntu.  ([http://www.guacosoft.com/attic/](http://www.guacosoft.com/attic/))  

The instructions are to run it from the terminal.  That's ok for once and a while, but a pain if used regularly.  So I tried to set up a launcher for it.  I couldn't seem to get it to work.  In the command, I simply put in the path and file name, but can't seem to get it to work.

Any ideas?

Thanks.

---

### Post by pbrane on 2010-04-04
According to the website you should run **run-attic.sh**, so in the *Command* section of the Create Launcher dialog you should have something like */home/user/run-attic.sh*. Assuming you unzipped it in your home directory. Just make sure you use the complete path to the script.

---

### Post by new_tolinux on 2010-04-04
> **pbrane said:**
> According to the website you should run **run-attic.sh**, so in the *Command* section of the Create Launcher dialog you should have something like */home/user/run-attic.sh*. Assuming you unzipped it in your home directory. Just make sure you use the complete path to the script.

Sometimes that worked for me.
Sometimes it didn't. To get it working I needed *sh /path/to/script.sh* as run command.

---

### Post by pbrane on 2010-04-06
If you needed to run *sh /path/to/script.sh* then *script.sh* may not be executable. You can try **chmod +x script.sh**. You may need to use sudo to do that if the script is not in a directory you have write access to.

---

