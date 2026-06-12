---
title: "Alacarte isn't working"
date: 2009-12-31
forum: General Help
---

### Post by SchizmWolf on 2009-12-31
Hi, I'm running Kubuntu Jaunty 9.04. I found out whilst trying to install Alien Arena that Kubuntu doesn't have the alacarte menu editor built in, so I got it via sudo apt-get install. Well, it opens, but whenever I try and "add item", it spits this out in the terminal:

```
Traceback (most recent call last):   
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 308, in on_new_item_button_clicked                                                     
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)                                                                        
  File "/usr/lib/python2.6/subprocess.py", line 595, in __init__               
    errread, errwrite)                                                         
  File "/usr/lib/python2.6/subprocess.py", line 1092, in _execute_child        
    raise child_exception                                                      
OSError: [Errno 2] No such file or directory                                   
Traceback (most recent call last):                                             
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 295, in on_new_menu_button_clicked                                                     
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)                                                                        
  File "/usr/lib/python2.6/subprocess.py", line 595, in __init__               
    errread, errwrite)                                                         
  File "/usr/lib/python2.6/subprocess.py", line 1092, in _execute_child        
    raise child_exception                                                      
OSError: [Errno 2] No such file or directory                                   
Traceback (most recent call last):                                             
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 308, in on_new_item_button_clicked                                                     
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)                                                                        
  File "/usr/lib/python2.6/subprocess.py", line 595, in __init__               
    errread, errwrite)                                                         
  File "/usr/lib/python2.6/subprocess.py", line 1092, in _execute_child        
    raise child_exception                                                      
OSError: [Errno 2] No such file or directory                                   
Traceback (most recent call last):                                             
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 308, in on_new_item_button_clicked                                                     
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)                                                                        
  File "/usr/lib/python2.6/subprocess.py", line 595, in __init__               
    errread, errwrite)                                                         
  File "/usr/lib/python2.6/subprocess.py", line 1092, in _execute_child        
    raise child_exception                                                      
OSError: [Errno 2] No such file or directory                                   
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 308, inon_new_item_button_clicked
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)
  File "/usr/lib/python2.6/subprocess.py", line 595, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1092, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
```I don't even know where to begin here... I'm pretty new to Linux. Any help would really be appreciated, and hopefully I'll get some responses with this thread, unlike others I've posted, haha.

---

### Post by Pollox on 2009-12-31
I don't use KDE, but I would think if alacarte is not the built-in menu editor, then you shouldn't use it.  From a quick web search, it sounds like kmenuedit is the way to go.  I would be very surprised if Kubuntu doesn't have a built-in menu editor.

---

### Post by SchizmWolf on 2010-01-02
Thanks, Pollox. Turns out my kubuntu did come with kmenuedit included, but I've found I vastly prefer alacarte. It's UI is nicer, and I still can't figure out how to designate icons on a new item with Kmenuedit. So now I've a bunch of blank icons for programs I've created. Oh well, at least it's now just an aesthetics issue instead of a mini-crisis. Thanks!

---

