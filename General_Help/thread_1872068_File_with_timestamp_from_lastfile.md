---
title: "File with timestamp from lastfile"
date: 2011-10-30
forum: General Help
---

### Post by mybrain87 on 2011-10-30
I'd like to have a script, which creates a File "Lastfile", but takes not the current time bute the timestamp from the last file created in that directory.

so for example i run the script an 2 pm, but the last file was created at 1pm, so the newly generated file should have 1pm as its timestamp.


possible?

---

### Post by WasMeHere on 2011-10-30
Yes, mybrain87

Of course it's possible with your brains and Ubuntu ;-)

Try ```
rm Lastfile;for i in $(ls -tr);do Command=$(echo touch Lastfile -r "$i");done;$Command
``` It works for me: creating an empty file with the timestamp of the newest file in the current directory.

Have fun finding out :-)
Olle

---

### Post by mybrain87 on 2011-10-30
> **Olle Wiklund said:**
> Yes, mybrain87

Of course it's possible with your brains and Ubuntu ;-)

Try ```
rm Lastfile;for i in $(ls -tr);do Command=$(echo touch Lastfile -r "$i");done;$Command
``` It works for me: creating an empty file with the timestamp of the newest file in the current directory.

Have fun finding out :-)
Olle

OMG, thank you very much.

Seems so easy now that i see it. Still pretty new to ubuntu and the commandline.

---

### Post by mybrain87 on 2011-10-30
Is there a way to ignore directories, and just look through the files to find the last modified file not directory.

I need that because lftp doesn't copy the timestamps for directories but it does for files and i need to have a file with the time stamp of the last modified file.

---

### Post by mybrain87 on 2011-10-30
okay figured that with ls -R -tr it should find the last modified file in all the directories and subdirectories.

but when i try 

for i in $(ls -R -tr);do Command=$(echo touch Lastfile -r "$i");done;$Command

it tells me touch: failed to get attributes of `Filename': No such file or directory

Anybody know whats wrong?

---

