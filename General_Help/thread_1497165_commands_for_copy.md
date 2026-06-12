---
title: "commands for copy"
date: 2010-05-30
forum: General Help
---

### Post by nischalinn on 2010-05-30
I want to **copy a file from my home folder to my desktop via terminal.** how can I do that? suppose I've a file name** source.txt** at my **home** folder and I want to copy it in my **desktop**, how can I do that?

Similarly, suppose I've a folder name** source** in my home and I want to copy it at my desktop in the folder name** destination,** how can I do that via terminal?

---

### Post by sisco311 on 2010-05-30
```
cp ~/source.txt ~/Desktop
```
```
cp -r ~/source ~/Desktop/destination
```

[uhelp]community/UsingTheTerminal[/uhelp]

---

### Post by lmarmisa on 2010-05-30
Try these commands:

> 

cp ~/source.txt ~/Desktop/

cp -r ~/source/ ~/Desktop/destination/

Other languages different to English may not use the name "Desktop".  For example, Spanish version uses "Escritorio".

---

