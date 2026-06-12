---
title: "7-zip"
date: 2009-10-23
forum: General Help
---

### Post by Elfo33 on 2009-10-23
I have many folders with multiple files in each folder.  I'd like to compress the contents in each folder into a 7z archive, and then save that 7z in the directory where the folder resides, not in the folder itself.  Is there a simple way to automate this?

---

### Post by Bachstelze on 2009-10-23
```
for i in *; do test -d $i && 7zr a $i.7z $i; done
```

---

### Post by martrn on 2009-10-23
> **Elfo33 said:**
> I have many folders with multiple files in each folder.  I'd like to compress the contents in each folder into a 7z archive, and then save that 7z in the directory where the folder resides, not in the folder itself.  Is there a simple way to automate this?

The only way two do this 'easily' would be to write a bash shell script.  Bash in the borne again shell for linux systems, and writing a bash (or any shell) script involves understanding a large amount of syntax for the bash shell. Well worth learning but it might take quiet a lot of time.

There are already a large amount of shell scripts already written for you to do this for example there is one at [http://r3dux.org/?p=439]("http://r3dux.org/?p=439").  When looking for scripts, not its a good way to get to learn a scripting language.

Alternative if you know php or perl you could write a php or perl script to do the same job, and php and perl scripts can be run from the cli or a terminal.

---

### Post by kanikilu on 2009-10-23
I use a small script to do the same thing, but it looks like Bachstelze has an even simpler solution :)

```
#!/bin/bash
for dir in *
 do
  if [ -d "$dir" ]
  then
    7za a "$dir".7z "$dir";
  continue
  fi
 done

```

*I'm writing this from memory, but I think that's basically what I use...

---

