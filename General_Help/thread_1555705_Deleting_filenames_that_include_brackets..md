---
title: "Deleting filenames that include brackets."
date: 2010-08-18
forum: General Help
---

### Post by zozza on 2010-08-18
I downloaded a file.  I then downloaded the same file again.  This meant the second file was called nameoffile(2).doc.  I cannot see to remove the file because of the brackets nor can I move it or rename it.    How can I dispose of it?  I have tried sudo with the various rm commands.  Thanks.

---

### Post by Vaphell on 2010-08-18
i don't think () should make any difference. What is the error message?

---

### Post by gmargo on 2010-08-18
The complicated way: Escape the special characters:
```

rm nameoffile\(2\).doc

```The simple way: Use quotes:
```

rm "nameoffile(2).doc"

```The Unix way: Use wildcards:
```

rm nameof*2*doc

```

---

### Post by Zorgoth on 2010-08-18
You could try 

find -name '*(*' -execdir rm {} \; (executed from as deep in the directory tree as you can, since this will delete ANY file with a '(' in its name in $PWD - so if you just opened a terminal and typed that command right away, every file with a '(' in your home directory or any of its subdirectories would be lost!)

Be warned that this is a very powerful command and you should make sure you know what you're doing.

---

### Post by gadolinio on 2010-08-18
> **Zorgoth said:**
> 
(...) executed from as deep in the directory tree as you can (...)

Be warned that this is a very powerful command and you should make sure you know what you're doing.

Right. Even more if you use any command other than:
rm "nameoffile(2).doc"
as gmargo suggested. This command deletes only that file, so it is the less dangerous one; just be careful while typing.
I am also wondering what do the "()" have to do with this.

---

### Post by LowSky on 2010-08-18
> **gmargo said:**
>  Use quotes:
```

rm "nameoffile(2).doc"

```The Unix way: Use wildcards:
  

Best option in my opinion

---

### Post by Zorgoth on 2010-08-18
Ah I did not read the initial post closely enough - i thought the op was trying to delete lots of files with brackets - don't ask me why, im stupid.

---

