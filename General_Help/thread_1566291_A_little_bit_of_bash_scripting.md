---
title: "A little bit of bash scripting"
date: 2010-09-02
forum: General Help
---

### Post by meadhikari on 2010-09-02
I want a bash script that copy's all files in my desktop that are not touched for a week and move it to some other location.

I am pretty new to bash scripting.

I could get the file list of my desktop but how to get their time and move them to some other location.

Please help me in decomposing and in solving this.

---

### Post by spjackson on 2010-09-02
A fair starting point would be something like
```

find ~/Desktop -maxdepth 1 -type f -atime +7

```A file has 3 timestamps: creation time, modification time, access  (read) time, for which you use one of -ctime, -mtime, -atime. This will  give you a list of files (not directories) on your Desktop (not in  sub-directories) that were last accessed (read) 7 or more days ago.

Then, what do you want to do with these files? Is it to copy them or to  move them (removing them from your desktop)? One thing to beware of if  copying and using access time, is to copy via a method that does not  change the access time!

---

### Post by nothingspecial on 2010-09-02
```
 find $HOME/Desktop -maxdepth 1 -mtime +7 -type f -exec mv {} /new/location/ \;
```ought to do it.

[I][B]Oh yes, don`t foreget the maxdepth or find will go through every directory on your desktop also...........unless you want it to
[/B][/I]

---

### Post by dv3500ea on 2010-09-02
The ```
mv FILE DESTINATION
``` command can move files.
The ```
stat -c %Y FILE
``` can find the last time that the file was modified.
The ```
date +%s
``` command can find the current time.

All you need to do is use the mv command to move each file if current time - file modified time > 7*24*60*60.

**EDIT: having seen what other people have said, their solution is simpler. I didn't realise the find command had this inbuilt ability.**

---

