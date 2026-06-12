---
title: "Executing script problem"
date: 2010-10-28
forum: General Help
---

### Post by drz4007 on 2010-10-28
Hello guys. When I double click on the script nothing happens. If t try to run it through terminal, it runs ok. In the Previous Ubuntu version (10.04) when  I double-clicked a script it popped up some choices. Run in terminal, display, etc. That does not happen now. Any ideas?

---

### Post by WorMzy on 2010-10-28
First thing's first, does the file have execute permissions?

```
ls -l <filename>
```

will tell you something like

```
-rw**_x_**rw**_x_**r-**_x_** 1 wormzy users   42083 Oct 26 19:11 <filename>
```

The x's mean that it has execute permissions. If the file doesn't, you can add them with:
```
chmod +x <filename>
```

If that's all fine and it still doesn't ask you what to do, then the next thing to check is your Nautilus settings. Open up a nautilus window and click Edit -> Preferences -> Behaviour, and make sure that "Ask each time" is selected for executable text files.
[IMG]http://img838.imageshack.us/img838/6861/20101028130244386x517sc.png[/IMG]

---

### Post by drz4007 on 2010-10-28
Thanx man. It was the nautilus behavior... Thanx a lot.

---

