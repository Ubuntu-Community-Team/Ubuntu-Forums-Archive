---
title: "Executing Python from right click"
date: 2010-12-15
forum: General Help
---

### Post by ki4jgt on 2010-12-15
Is there a way I can execute a *.py file by right clicking on it, instead of having to python *.py

---

### Post by VCoolio on 2010-12-15
Make the file executable (chmod +x .../file.py), then click it. Make sure the preferences of nautilus (if you use that as your file manager) for executable files are set to execute them (edit > preferences > behavior I think it is).

---

### Post by surfer on 2010-12-15
you can make the file executable (in the shell with $ chmod u+x filename.py, or with nauilus: properties -> permissions -> allow executing file as program). then double-clicking should run it.

this will not open a terminal for you. so for a program requiring input and writing output to sys.stdout (with print) this will not work.

also make sure your python file starts with
```
#!/usr/bin/python
```

---

### Post by flyingbear on 2010-12-15
Just add this as first line in your script file ```
#!/usr/bin/env/python
```Then make the file executable```
sudo chmod 755 script.py
```

---

### Post by ki4jgt on 2010-12-15
Is there anyway to get it to open the Terminal automatically? :-(

---

### Post by VCoolio on 2010-12-15
something like
gnome-terminal -e .../file.py
should do it. Create a launcher with that command or use a [nautilus script](https://help.ubuntu.com/community/NautilusScriptsHowto?highlight=%28%28NautilusScriptsHowto%29%29).

---

### Post by surfer on 2010-12-15
yes, you can create a bash script opening a terminal and running the file for you. make it executable as well. it should look something like this:
```
#!/bin/bash

/usr/bin/gnome-terminal -e ./test.py

```

---

### Post by ki4jgt on 2010-12-15
gracias

---

### Post by surfer on 2010-12-16
de nada!

would you please mark the thread as solved if you think your question was answered?

---

