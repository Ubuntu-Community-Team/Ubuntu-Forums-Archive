---
title: "Need idiot proof instructions to repair zip."
date: 2011-04-28
forum: General Help
---

### Post by webcabbie on 2011-04-28
o.k. me big dummie. 

I have a file on my desktop named hey.zip

When I try to unpack it I get this


7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.utf8,Utf16=on,HugeFiles=on,1 CPU)

Error: /home/michael/Desktop/hey.zip: Can not open file as archive

Errors: 1

Any idiot proof instructions to fix it?

---

### Post by CharlesA on 2011-04-28
It's probably corrupted. I don't know of any way to repair a corrupt zip outside of restoring it from backups.

---

### Post by oldos2er on 2011-04-28
You can try ```
zip -FF hey.zip
``` no guarantees it'll work though.

---

### Post by webcabbie on 2011-04-28
michael@michael-desktop:~$ zip -FF hey.zip
	zip warning: fix options -F and -FF require --out:
                     zip -F indamagedarchive --out outfixedarchive

zip error: Invalid command arguments (fix options require --out)


?

---

### Post by CharlesA on 2011-04-28
Try this:

```
zip -F hey.zip --out repair.zip
```

---

### Post by webcabbie on 2011-04-29
michael@michael-desktop:~$ zip -F hey.zip --out repair.zip
Fix archive (-F) - assume mostly intact archive
	zip warning: No .zip file found
        (If all you have are splits (.z01, .z02, ...) and no .zip, try -FF)
zip I/O error: No such file or directory
zip error: File not found or no read permission (hey.zip)
michael@michael-desktop:~$

---

### Post by imigueldiaz on 2011-04-29
> **webcabbie said:**
> michael@michael-desktop:~$ zip -F hey.zip --out repair.zip
Fix archive (-F) - assume mostly intact archive
	zip warning: No .zip file found
        (If all you have are splits (.z01, .z02, ...) and no .zip, try -FF)
zip I/O error: No such file or directory
zip error: File not found or no read permission (hey.zip)
michael@michael-desktop:~$

Try

```

michael@michael-desktop:~$ cd Desktop
michael@michael-desktop:~/Desktop$ zip -F hey.zip --out repair.zip

```

Best

---

