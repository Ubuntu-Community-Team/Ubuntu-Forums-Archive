---
title: "error when updating......."
date: 2009-07-30
forum: General Help
---

### Post by jaw175 on 2009-07-30
This error came up after trying to get a package using Add/Remove. I've tried to fix it using the instruction, using the terminal,but to no avail  as,being an elderly novice who can't get his head around using the CLI, I'm stuck. Now I find its also stopping an updating through package manager.
Any help to fix the problem would be most appreciated. And thanks! :)
Wills.

This is the offending menu item.........[http://ubuntuforums.org/attachment.php?attachmentid=122978&stc=1&d=1248977058](http://ubuntuforums.org/attachment.php?attachmentid=122978&stc=1&d=1248977058)

---

### Post by DaithiF on 2009-07-30
Hi,
Lets try running the fix from the command line again:
Open a terminal:
Applications -> Accessories -> Terminal

type in this (exactly!)
```
sudo dpkg --configure -a
```
and hit Return

Note there is a space before the final -a

if any errors are reported, paste them in a reply here, and we'll see what we can do.

---

### Post by jaw175 on 2009-07-30
Hi Daithif, Followed your instruct. This is the outcome from terminal.....

wills@self-desktop:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
wills@self-desktop:~$ sudo dpkg --configure -a
[sudo] password for wills: 
Setting up java-common (0.30ubuntu4) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
wills@self-desktop:~$ 

Sorry to say that I don't really understand the output and will await your view of it. Thank you for your response. :)

Wills.

---

### Post by DaithiF on 2009-07-30
Hi Wills,
that looks just fine, no errors reported.  You can close the terminal.  I would suggest you  go into System->Preferences->Update Manager and Install whatever updates may be listed there, but otherwise your problem should be resolved.

---

### Post by jaw175 on 2009-07-30
Hi DaithiF, You were correct! Just completed the Update as you suggested. 40 GB+...Security & Recommended Updates. No problems with that...& more to the point I'm happy that it keeps my system 'clean'. Thanks very much for your help...it's much appreciated. :)  Regards,

Wills.

---

### Post by DaithiF on 2009-07-31
Hi Wills, happy to help.

---

