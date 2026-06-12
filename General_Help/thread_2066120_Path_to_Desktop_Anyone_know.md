---
title: "Path to Desktop? Anyone know?"
date: 2012-10-03
forum: General Help
---

### Post by listerdl on 2012-10-03
I need to run a python script from my linux ubuntu desktop and I have forgotten the correct path - 

** If the python file is on my DESKTOP do I input this in terminal?

python /home/(user)/Desktop file.py

*-- or ---*

python ~/Desktop/file.py 

Thanks

---

### Post by drmrgd on 2012-10-03
The notation '~/' is the BASH shortcut for /home/username/.  So, I believe either should work if your file is on your Desktop.  If you use the full path, don't forget the slash between "Desktop" and your file name:

```
python /home/(user)/Desktop**/**file.py
```

---

