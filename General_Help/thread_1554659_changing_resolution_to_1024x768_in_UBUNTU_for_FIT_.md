---
title: "changing resolution to 1024x768 in UBUNTU for FIT PC 1.0"
date: 2010-08-17
forum: General Help
---

### Post by praveenkovvuri on 2010-08-17
[SIZE=4]hi ,i m using fit pc 1.0 with ubuntu 9.04. i had my maximum resolution as 800x600 with 60 HZ and now i want to increase my screen resolution to 1024x768 with 60HZ. can anybody plz help me out with this?[/SIZE]

---

### Post by realzippy on 2010-08-17
Welcome!
That depends on the graphics card you use.Can you [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal") 
and type

```
lspci | grep VGA
```

please post the output....

---

### Post by praveenkovvuri on 2010-08-17
[SIZE=3]The Output for lspci |grep VGA  command is 

00:01.1 VGA compatible controller: Advanced Micro Devices [AMD] Geode LX Video

Is this VGA compatible for this resolution?
[/SIZE]

---

### Post by realzippy on 2010-08-17
1.Sure your display's resolution is "1024x768" and not "1024x600" ?
  (or: "what is the exact name of the laptop?")

2.Post your xorg.conf file (if exists).To do so,type in terminal:

  ```
gedit /etc/X11/xorg.conf
```

  and post content here.

3.Open terminal,type
 
  ```
xrandr
```

  and post output please.

4.Can you decrease the letter size in your postings?   ;)



EDIT:
Just saw your post [http://ubuntuforums.org/showthread.php?t=895259;](http://ubuntuforums.org/showthread.php?t=895259;)
if problem is solved,please mark thread as "solved" (Threadtools)
and comment your solution.....

---

