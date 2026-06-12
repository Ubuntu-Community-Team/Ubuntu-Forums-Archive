---
title: "Help with a text copying script"
date: 2011-09-12
forum: General Help
---

### Post by Enigmapond on 2011-09-12
I had to re-install a bit ago and backed up a folder with subfolders to my NTFS partition. The only thing in these folders were text files. Now when I go to open, as usual with gedit, they don't open until I make new text files for them all. Unknown as to how this happened. What I need is a script I can run on the main folder to include all the texts in the sub-folders, and just copy and rename the file with a different suffix like "_1" or something and delete the original. I hope I have explained this well enough.

Thanx!

---

### Post by SoFl W on 2011-09-12
If you are looking to rename multiple files I would suggest "GPRename" from the software center.
I think it would be better to find out what caused the problem in the first place.

---

### Post by Enigmapond on 2011-09-12
Thanks for that but the problem isn't ongoing, just happened to the files I had backed up. Everything works normal otherwise. I'll try that...I was just trying to save some time with a script rather than a GUI... :)

---

### Post by Enigmapond on 2011-09-12
Also simply re-naming the file doesn't help. It still won't open with gedit, my default.

---

### Post by sisco311 on 2011-09-12
Check out BashFAQ #30 (link in my signature).

Try something like:
```
cd path/to/dir
find ./ -iname '*.txt' -type f -execdir mv -b -- '{}' '{}'_1 \;
```
this will rename the .txt files to .txt_1.


This one will copy the files and remove the original. Be careful, test it and backup your files:
```

find ./ -iname '*.txt' -type f -execdir bash -c 'cp -b -- "$1" "${1}_1" && rm "$1"' _ '{}' \;

```

---

### Post by Enigmapond on 2011-09-12
> **sisco311 said:**
> Check out BashFAQ #30 (link in my signature).

Try something like:
```
cd path/to/dir
find ./ -iname '*.txt' -type f -execdir mv -b -- '{}' '{}'_1 \;
```

It didn't work. Well..it added a _1 at the end but they still won't open even though gedit is still set to open it. Thanx for the effort though..:)

No go on the second as well.. :( Guess I'll just do it manually. I have a few hours to kill.. :)

---

### Post by WorMzy on 2011-09-12
Why don't they open? Does gedit give an error message? Does stdout or stderr have anything to say about it (open the files from a terminal).

---

### Post by sisco311 on 2011-09-12
What do you have to do in the GUI to fix the files?

---

### Post by Enigmapond on 2011-09-12
They open fine in the terminal it's just when I click on them they don't...ODD I know. I just need to copy the file to a newly created .txt file with a different suffix like _1.txt and delete the original. As I've done that manually and it works...thanks again for the assist! :)

---

### Post by sisco311 on 2011-09-12
Maybe it's a permission issue and your file manager tries to execute the files instead of opening them.

---

### Post by Enigmapond on 2011-09-12
> **sisco311 said:**
> Maybe it's a permission issue and your file manager tries to execute the files instead of opening them.

Ok..well that does it if I give it the option to ask whether to display or execute. I had it set to run execs when clicked. I choose display and it opens right up. I'll just keep that option in Nautilus. Thank you ever so....

---

### Post by sisco311 on 2011-09-12
Cool! I'd remove the execute permissions, not sure if you can do it recursively via the GUI, in CLI you can try:
```
find **path/to/dir** -name \*.txt -type f -exec chmod -x '{}' +
```

where **path/to/dir** is the actual path to the directory.

---

### Post by Enigmapond on 2011-09-12
> **sisco311 said:**
> Cool! I'd remove the execute permissions, not sure if you can do it recursively via the GUI, in CLI you can try:
```
find **path/to/dir** -name \*.txt -type f -exec chmod -x '{}' +
```where **path/to/dir** is the actual path to the directory.

Me=Idot...
LOL Ok even better. I did that and removed the execute on the whole directory and they open as normal...now as to why that was changed?...who knows but it's fixed. Thanx...there are over 1000 files there.. :)

Thanks again!

---

### Post by sisco311 on 2011-09-12
NTFS partitions don't support Unix/Linux file permissions. The permissions are set at mount time for every file and directory. 

How do you mount the partition? In fstab you can use the fmask/dmask mount options to cheange the permissions.

If you want to preserv the permissions and ownership of your backups, then backup them in a tar archive.

---

### Post by Enigmapond on 2011-09-12
> **sisco311 said:**
> NTFS partitions don't support Unix/Linux file permissions. The permissions are set at mount time for every file and directory. 

How do you mount the partition? In fstab you can use the fmask/dmask mount options to cheange the permissions.

If you want to preserv the permissions and ownership of your backups, then backup them in a tar archive.
Ok...right I just copied the file over before the re-install. Thanks for the info for future reference. At least I know HOW it happened now.. :)

---

### Post by sisco311 on 2011-09-12
You are welcome!

---

