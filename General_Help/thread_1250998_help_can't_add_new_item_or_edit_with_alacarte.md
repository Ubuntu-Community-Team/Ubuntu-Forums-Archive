---
title: "help can't add new item or edit with alacarte"
date: 2009-08-27
forum: General Help
---

### Post by astrakhan on 2009-08-27
hi, im having no luck editing menus with alacarte in jaunty. I cant add new items either. But all other buttons work. i've checked permissions and they seem ok, however when alacarte is opened in a terminal and i click on new item it returns this:

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 308, in on_new_item_button_clicked
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)
  File "/usr/lib/python2.6/subprocess.py", line 595, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1092, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory


if i click on properties it just doesn't do anything.

---

### Post by mikasogh on 2011-01-15
> **astrakhan said:**
> hi, im having no luck editing menus with alacarte in jaunty. I cant add new items either. But all other buttons work. i've checked permissions and they seem ok, however when alacarte is opened in a terminal and i click on new item it returns this:Traceback (most recent call last):File "/usr/lib/python2.6/dist-packages/[[COLOR=#000000]Alacarte[/COLOR]](http://www.powdershell.com/cs/fitness/5-points-to-ignite-your-quick-weight-loss-diet.html)/MainWindow.py", line 308, in on_new_item_button_clickedprocess=subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)File "/usr/lib/python2.6/subprocess.py", line 595, in __init__errread, errwrite)File "/usr/lib/python2.6/subprocess.py", line 1092, in _execute_childraise child_exceptionOSError: [Errno 2] No such file or directoryif i click on properties it just doesn't do anything.It's very detailed, Thanks for your sharing! Now I got it.

---

