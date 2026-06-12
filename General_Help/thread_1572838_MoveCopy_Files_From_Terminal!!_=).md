---
title: "Move/Copy Files From Terminal!! =)"
date: 2010-09-11
forum: General Help
---

### Post by Arkish0 on 2010-09-11
hello!
im using ubuntu 10.04
sometimes i find more useful to use the terminal to copy or move folders or files to other directories (more important when they need admin permission)

today i tried to copy ALL files from a directory to another...
and i realized that i dont know... 
i know that that "~ mv /ThisThing/ /ThisFolder/" "~ cp /ThisThing/ /ThisFolder/" but howould i be able to copy EVERYTHING from a folder into another.
tis is diferent from copying the folder itself (which i also would like to know)

i bet is a simple thing that i havent figured out!

Thanks!

---

### Post by AlphaLexman on 2010-09-11
> **Arkish0 said:**
> ~ mv /ThisThing/ /ThisFolder/" "~ cp /ThisThing/ /ThisFolder/"

Should be:
> "mv ~/ThisThing/ ~/ThisFolder/" " cp ~/ThisThing/ ~/ThisFolder/"

---

### Post by wojox on 2010-09-11
If your new to Linux I would stick to copying

```
cp -R [from dirctory] [to directory] 
```

---

### Post by Tylerjd on 2010-09-11
You can use the -r option to copy folders/files recursively. like:
```
cp -r ~/ThisFolder ~/ThatFolder
```
and the same goes with mv. (**The -r can be replaced with -R)

To copy the contents of a folder to another it would be:
```
cp -r ~/ThisFolder/* ~/ThatFolder/
```
and again, the same goes with mv

---

### Post by AlphaLexman on 2010-09-11
> **Tylerjd said:**
> and again, the same goes with mv

Actually, 'mv' does NOT have the -r (recursive) option.

---

### Post by Arkish0 on 2011-04-24
Thanks to all =) that did it!

---

