---
title: "extract multiple files from multiple folders"
date: 2012-04-15
forum: General Help
---

### Post by tadcan on 2012-04-15
What bash command would search through a folder with multiple folders and extract *.ttf to a single folder?

---

### Post by sohlinux on 2012-04-15
from the current directory try the following but make a backup before you try it!

copy
```
find . -name "*.ttf" -exec cp "{}" /dir \;
```

move
```
find . -name "*.ttf" -exec mv "{}" /dir \;
```

---

### Post by Dreamer Fithp Apprentice on 2012-04-15
deleted by edit, because on rereading I realize I misunderstood the question. Please ignore this dumb post.

---

### Post by tadcan on 2012-04-15
Thanks. I remember reading that the copy command also pastes? Just need to find where they ended up.... :)

---

### Post by Vaphell on 2012-04-15
.bash_history file stores commands you entered

```
grep 'find.*-exec' .bash_history
```

---

### Post by papibe on 2012-04-15
+1 for sohlinux's solution.

However, I would add a little cavet: since you'll be copying or moving from several directories, it is possible that two different files have the same file name. For instance:
```
$ ls -R
file.ttf
adir/file.ttf
```
Then when moved or copied to dir/, they will be overwritten (just the last one will survive). As a safe measure, you can use the -b option (either on cp or mv). That will create a copy of the file before overwritten it.

For example:
```
find . -name '*.ttf' -exec mv **[COLOR="Red"]-b[/COLOR]** '{}' dir/ \;
```

Cavet's cavet: sadly this will only save the last two copies. If there's a 3rd, or more, file with the same filename, just the last two will survive.

Just s few thoughts.
Regards.

---

### Post by tadcan on 2012-04-15
I did a backup so duplicates won't be an issue. No duplicate files turned up. The grep command gave a no file found.

```
find . -name '*.ttf' -exec mv -b '{}' dir/ \;
```
returned (the last example)
```
mv: cannot move `./lora/Lora-BoldItalic.ttf' to `dir/': Not a directory

```
Which is odd because it worked the first time.
When I went to nautilus and put in /dir no dir was found. Should mkdr be used to create an output folder?

---

### Post by papibe on 2012-04-15
The target directory has to exist.

In sohlinux's example it was /dir Thats a directory under the root directory (/).

Sorry if I created confusion, but in my example I used a local directory just under the command is executed. To created that directory run:
```
mkdir dir
```
I hope that clarify things a little bit.
Regards.

---

### Post by tadcan on 2012-04-16
Thanks that worked. 
```
find . -name '*.ttf' -exec mv -b '{}' /home/*username*/Documents/newfonts \;
```

Could someone explain all the parts of that command.

---

### Post by Vaphell on 2012-04-16
find <dir> -name <filenames-pattern>
-exec = for each found object perform the following:
mv -b {} destination_dir
{} is a placeholder for the name of the found object
-exec is ended with escaped \; or ';' so it knows where the inner command ends

---

