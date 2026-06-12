---
title: "can't create new folder in system files (not even in terminal)"
date: 2011-03-17
forum: General Help
---

### Post by Quazze on 2011-03-17
Hello

I don't seem to be able to create a new folder in my system files. I know I have to do this in the terminal as root, but I always get the answer that it cannot create the directory because there is no such file or directory. Yet the directory where I want to make the new folder definitely exists (I even just go there and try to create the folder)

Here is the exact code:
```

lukas@lukas-VGN-FZ21E:/proc/asound/card0/pcm0p$ sudo mkdir oss
mkdir: cannot create directory `oss': No such file or directory
```

Any ideas?

---

### Post by Sina_RJ on 2011-03-17
are you sure you have completely entered direction correct?
are you right in spelling capital words at beginning?

EDIT: silly question,and *sisco311* is right!

---

### Post by sisco311 on 2011-03-17
> **Quazze said:**
> Hello

I don't seem to be able to create a new folder in my system files. I know I have to do this in the terminal as root, but I always get the answer that it cannot create the directory because there is no such file or directory. Yet the directory where I want to make the new folder definitely exists (I even just go there and try to create the folder)

Here is the exact code:
```

lukas@lukas-VGN-FZ21E:/proc/asound/card0/pcm0p$ sudo mkdir oss
mkdir: cannot create directory `oss': No such file or directory
```

Any ideas?

[/proc]("http://en.wikipedia.org/wiki/Procfs") is a virtual filesystem, so I'm not surprised...

What's your goal? Why are you trying to create a directory under /proc?

---

### Post by Quazze on 2011-03-17
yes I'm sure. I can copy the directory from the properties. And still, the problem can't be a wrong directory, because I just go in the directory (in the terminal ofcourse) and then do the mkdir command.

Even when I go in a lower directory like just /proc, it doesn't work... :s

---

### Post by Quazze on 2011-03-17
well the goal is not actually making that dir, but I actually wanted to do this:

> sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exitwhich is a suggested solution for a sound problem for Enemy Territory ([https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory))
But I also got the answer "no such file or directory", so I got curious/confused/frustrated and tried to find out what the problem was.

---

