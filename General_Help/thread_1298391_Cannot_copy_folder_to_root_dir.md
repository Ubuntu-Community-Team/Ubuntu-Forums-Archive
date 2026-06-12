---
title: "Cannot copy folder to root dir"
date: 2009-10-22
forum: General Help
---

### Post by NMWindows on 2009-10-22
Hello All, 

I am having a problem trying to copy a folder into the root directory from the desktop, the command I used was "Cp -r" but it keeps telling me:

*cp: missing file operand*

what do I need to do?

---

### Post by tetsuoharry on 2009-10-22
```
sudo cp file newloaction
```

or

```

sudo cp -rf file newlocation
```

eg
```

sudo cp -rf file.new /
```

to copy file.new to into / to copy it recursively ie the folder and its contents and to force it

---

### Post by NMWindows on 2009-10-22
I got it, I had to add the target directory.

So, it is 

cp -r sourcedir targetdir 

thanks for the help

---

