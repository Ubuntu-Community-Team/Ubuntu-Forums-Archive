---
title: "clipboard commands in CLI"
date: 2009-10-01
forum: General Help
---

### Post by rogerdean on 2009-10-01
Hello all

Does anyone know the CLI command I would use to copy the entire contents of a text file (not the file itself) into my clipboard?

Many thanks
Roger

---

### Post by diesch on 2009-10-01
```

xclip -i your_file

```

xclip is in universe and not installed by default

---

### Post by sisco311 on 2009-10-01
or xsel: 

```
sudo apt-get install xsel
```

```

cat path/to/file | xsel -ib        # "copy"
xsel -ob                           # Ctrl(+Shift)+V or Right Click -> Paste

```   

or
```

cat path/to/file | xsel -i         # "copy"
xsel -o                            # middle mouse button 

```

---

### Post by rogerdean on 2009-10-01
Hi diesch, thanks for that. xclip was the first thing I tried, but it seems to put things in the xclip clipboard rather than the main clipboard. ie I need to use 'xclip -o' to get the content out again...

sisco, will have a look at yours, thanks

EDIT apologies diesch, xclip seems to work fine too. many thanks to you both

---

