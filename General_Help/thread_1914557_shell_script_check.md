---
title: "shell script check"
date: 2012-01-24
forum: General Help
---

### Post by wog on 2012-01-24
I just need another pair of eyes to go over this script, because I don't really know what I'm doing, and something seems to have changed since an upgrade ago.

The error I get when I run the script is:
rsync: link_stat "/home/james/Downloads/minecraft/world_storage/\#015" failed: No such file or directory (2)

When I look at the directory structure, it seems correct.
In the header for the Command Line window it reads: "~/Downloads/minecraft".
In the GUI window the directory structure reads "Home" instead of "james", but otherwise it's the same directory tree.
I know that "~" is "/home/james", but the script apparently thinks otherwise. Can someone please give me some advice?

----[Start]----
#backup script
RAM="/home/james/Downloads/minecraft/world/"
HDD="/home/james/Downloads/minecraft/world_storage/"
BAK="/home/james/Downloads/minecraft/world.bak/"

rsync -r -t -v "$RAM" "$HDD"
rsync -r -t -v "$HDD" "$BAK"
----[End]----

---

### Post by drmrgd on 2012-01-24
It looks like script for some unknown reason is inserting a carriage return character at the end of that line, and it's choking rsync.  How were you editing the file?  I think Windows has a habit of doing that natively.

You could try to rewrite the script in something like nano or vi to see if it eliminates the auto CR character at the end of the line.

---

### Post by sisco311 on 2012-01-24
never mind

---

### Post by wog on 2012-01-24
Thank you, Drmrgd. It appears I was editing the file in notepad, and it was adding character returns. I opened it in Focuswriter (for some reason I can no longer access gedit) and deleted the last two characters, typed them over and saved. The script now works, and no error messages. Hooray! :)

---

