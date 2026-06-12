---
title: "preserve a copy of all of the system-level configuration files"
date: 2009-07-07
forum: General Help
---

### Post by wiso2010 on 2009-07-07
[COLOR=black][FONT=Verdana]**How can I preserve a copy of all of the system-level configuration files** that end with **“.conf”.  **(Note that these files may be found in many directories, not just in **/etc**.) Use the **tar **utility to bundle these files into one file in the **/backup/system.config/** directory (or another directory of your choice), and compress the resulting file with the  **bzip2** compression utility. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]Any help will be great[/FONT][/COLOR]

---

### Post by sedawk on 2009-07-07
First to generate that list run
[CODE]
sudo find / -name \*.conf -print
[CODE]

If you output the list to a file you can run
tar with the "--files-from" option.

(Some people like to use "cpio" instead of "tar" in this
 situation because the output of "find" can be directly
 piped to a proper "cpio" command.
 It should also be possible to use rsync to create a backup
 directory containing only copies of \*.conf files and then to tar that
 backup directory)

---

### Post by wiso2010 on 2009-07-07
Ok this command worked but how can I u[COLOR=black][FONT=Verdana]se the **tar **utility to bundle these files into one file in the **/backup/system.config/** directory (or another directory of your choice), and compress the resulting file with the  **bzip2** compression utility[/FONT][/COLOR]

---

