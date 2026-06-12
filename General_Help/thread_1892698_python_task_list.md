---
title: "python task list?"
date: 2011-12-08
forum: General Help
---

### Post by LuniTux on 2011-12-08
Hello,

I would like to get a list of tasks that are in the taskbar using pygtk. I looked at the source code for python panel but could not figure it out. How would I get the listed programs?

ex:

Ubuntu Forums - Opera
lunitux - File Browser
test.py - /home/lunitux/python - geany
python - File Browser
lunitux@desktop: ~

(This is what currently appears in my gnome-panel)

Thanks

---

### Post by thaelim on 2011-12-08
If you wanted to do this directly in Python, it is unfortunately a very complicated task. However, you could try the app 'wmctrl' which can list windows in the way you are looking for. You could run wmctrl from your Python program using the subprocess module and read the output to get the list of windows.

---

### Post by LuniTux on 2011-12-08
I think that will work.

Thanks

---

