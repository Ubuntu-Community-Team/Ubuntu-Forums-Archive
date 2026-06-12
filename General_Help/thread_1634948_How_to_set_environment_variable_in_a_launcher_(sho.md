---
title: "How to set environment variable in a launcher (shortcut in windoze)"
date: 2010-12-01
forum: General Help
---

### Post by rbanavara on 2010-12-01
Hi

I am trying to create a launcher which runs virtual box from a custom config directory. For this I have to set an environment variable first then call VirtualBox command. From terminal it looks like:

```

helena@mint ~ $ export VBOX_USER_HOME=/mnt/shared/VirtualBox/
helena@mint ~ $ nohup VirtualBox > /dev/null 2> /dev/null &
```

If I have to create a shortcut for this, I am not sure how to define variable & call the command in a single command. There are some examples on:

[http://ubuntuforums.org/archive/index.php/t-437140.html](http://ubuntuforums.org/archive/index.php/t-437140.html)
[http://ubuntuforums.org/archive/index.php/t-867506.html](http://ubuntuforums.org/archive/index.php/t-867506.html)

like:

```
"DISPLAY=:0 xterm"
```

but when I try this, it wont work. My test.Desktop entry (I have started x on :1):

```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Icon[en_SG]=gnome-panel-launcher
Name[en_SG]=test
Exec=DISPLAY=:1  xclock
Name=test
Icon=gnome-panel-launcher

```

---

### Post by mc4man on 2010-12-01
Have no clue as to what you're actually doing but if I wanted to export in a launch command I'd use env <whatever> <com>

Alternately, if you can create a small script to do what you wish then just use the script as the launch command, either /path/to/scriptname or if it's in a /bin in your path just the scriptname itself

---

### Post by rbanavara on 2010-12-02
exactly what I was looking for...!

thank you mc4man

I have the launcher as shown in following image and it works perfectly:

[img]http://s3.postimage.org/ekbqbyuc/launcher.png[/img]

---

