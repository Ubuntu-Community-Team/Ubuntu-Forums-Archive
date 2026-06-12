---
title: "Command Line Question"
date: 2011-10-08
forum: General Help
---

### Post by johntkucz on 2011-10-08
lets say I have a folder 10 files

file1
file2
...

how could I from the command-line rename all 10 files prepending them with an underscore "_" (so they move to the top of the folder alphabetically.

Thanks!

---

### Post by haqking on 2011-10-08
> **johntkucz said:**
> lets say I have a folder 10 files

file1
file2
...

how could I from the command-line rename all 10 files prepending them with an underscore "_" (so they move to the top of the folder alphabetically.

Thanks!

```
man rename
```

I could type the syntax but prefer to give people the fishing rod to catch their own fish ;-)

---

### Post by speedwlk on 2011-10-08
I second haqking's opinion. 

Just note that, while using rename command, you might have to work a bit with perl expressions.

---

### Post by Dangertux on 2011-10-08
or just use a bash for loop

```

for i in file* ; do mv "$i" "${file/i}" _file; done

```

---

### Post by haqking on 2011-10-08
> **Dangertux said:**
> or just use a bash for loop

```

for i in file* ; do mv "$i" "${i/file*}" _file; done

```

poser ;-)

---

### Post by Dangertux on 2011-10-08
haters gonna hate :-P

---

### Post by haqking on 2011-10-08
> **Dangertux said:**
> haters gonna hate :-P

before anyone reports abuse....me and dangertux the poser ;-) are quite happy and are not arguing....LOL

---

