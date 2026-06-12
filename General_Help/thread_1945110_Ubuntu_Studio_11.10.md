---
title: "Ubuntu Studio 11.10"
date: 2012-03-22
forum: General Help
---

### Post by ZoxX on 2012-03-22
:confused:I upgraded Ubuntu from 10.04 to 11.10 (through 10.10, 11.04). I had no problems with 10.04.
I did necessary Script-Fu adjustments, set my preferable appearance, worked with Firefox and Thunderbird. At one moment I pressed Alt+F4 (Windows habit) and suddenly application closed (as expected) and Launcher disappeared as well as top desktop menu (File Edit View Go Bookmarks Help). There was just plain wallpaper background.
Reboot didn't help much. Still there was no Launcher. Top desktop menu (File Edit View Go Bookmarks Help) was there (but without icons, clock, net, shutdown). Using the menu I can start applications from /usr/share/applications. This is how I'm using Firefox right now.
I tried to reboot from previous Ubuntu installation but it didn't work out.
Is there any kind of Repair action I can use?

---

### Post by grahammechanical on 2012-03-22
There are two things that you can try

1) Alt+F2 and the command

```
unity
```

2) in a terminal (if you can)

```
unity & disown
```

Regards.

---

### Post by ZoxX on 2012-03-22
> **grahammechanical said:**
> There are two things that you can try

1) Alt+F2 and the command

```
unity
```

2) in a terminal (if you can)

```
unity & disown
```

Regards.

Thank you for your reply. Alt+F2 didn't work.
Yes I can use terminal. I installed something (Avant Window Navigator) and fill it with basic icons.
I guess I should type:
unity [Enter]
(and then)
disown [Enter]
I did the first and got:
zoxx@ubuntu:~$ unity
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing resize options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing move options...done
Initializing obs options...done
Initializing place options...done
Initializing animation options...done
Initializing vpswitch options...done
Initializing fade options...done
Initializing workarounds options...done
Initializing session options...done
Initializing showdesktop options...done
Initializing cube options...done
Initializing scale options...done
Initializing td options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing unitymtgrabhandles options...done
Initializing ezoom options...done
Initializing switcher options...done
Setting Update "command"
Setting Update "mode"
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "keep_minimized_windows"

---

### Post by ZoxX on 2012-03-23
I will call this Problem Solved.
I didn't solve the problem. Terminal [unity & disown] did nothing. Everything was as before. No menu icons, no Launcher.
I installed Avant Window Navigator to make Ubuntu usable. Now I'm using AWN in stead of Launcher. I will remove a menu as well.[http://ubuntuforums.org/images/smilies/smiley-faces-80.gif](http://ubuntuforums.org/images/smilies/smiley-faces-80.gif)

---

