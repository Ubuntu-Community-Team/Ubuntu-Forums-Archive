---
title: "Trying to launch a python command..."
date: 2011-10-19
forum: General Help
---

### Post by silverbullet007 on 2011-10-19
Ubuntu 11.10
Installed OpenXenCenter, now Im trying to make a launcher for window.py

First off I miss being able to right-click and create a launcher like a new file.  Not having it sucks, devs should bring it back.

Ok anyway, I'm having trouble figuring out the command syntax.

i.e. gnome-terminal --command python /home/Desktop/openxencenter/window.py

Just doesn't work.  Any thoughts?

---

### Post by spiky001 on 2011-10-19
Did you make the file executable ```
chmod +x file.py
```

---

### Post by papibe on 2011-10-19
If window.py starts with a line like this:
```
#!/usr/bin/env python
```
or this:
```
#!/usr/bin/python
```
You can call it directly:
```
/home/Desktop/openxencenter/window.py
```

I hope that helps,
Regards.

---

### Post by silverbullet007 on 2011-10-19
Calling it directly doesn't work.. "window.py: command not found"

Which also means making the fire executable doesn't work either.

however the file's contents, the first line is
```
#!/usr/bin/env python
```

---

### Post by wazzosan on 2012-05-02
Did you ever get anywhere with this?  I have been trying to setup the same thing without any luck.

gksu python /home/username/openxencenter/trunk/window.py


It asks me for my password but never launches the app.

---

