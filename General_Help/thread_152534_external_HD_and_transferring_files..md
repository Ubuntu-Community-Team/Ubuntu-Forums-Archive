---
title: "external HD and transferring files."
date: 2006-03-30
forum: General Help
---

### Post by moon_dog on 2006-03-30
how do you transfer files from the external HD to a directory you created?  using the windows, i can copy the files to my desktop but not to a directory i made in the root directory.  i tried moving files manually in the command line but i can't seem to enter the directory of my external HD.  the path is /media/WD Combo.  i can enter the media folder but not the WD Combo folder, it says the folder doesn't exist.  is there a special character i use like "_" instead of the space between "WD" and "Combo"?

i also can't move a file i have from my desktop to a folder.  i typed this in the shell "mv -i OOo_2.0.2_LinuxIntel_install_wJRE.tar.gz /test".  there's no error message, but the "mo@ubuntu:/$" just disappears, leaving me with ">" and a blinking cursor.

---

### Post by trent dillman on 2006-03-30
Spaces should be backslashed '\ '.

Or, you could try the '?' instead.

When typing names of files, try using 'TAB' for autocomplete, e.g. OO(TAB) will complete OOo_2.0.2_LinuxIntel_install_wJRE.tar.gz.

---

### Post by moon_dog on 2006-03-30
okay got it thanks.  how about .rpm files?  how do you run these files?  i just downloaded xfce and when i unzipped it it gave me a lot .rpm files, i don't know what to do with them.

---

### Post by trent dillman on 2006-03-30
xfce should be in the repos, so try installing with synaptic.

For the record, though, use alien to install rpms. You have to use fakeroot or sudo, though.

---

