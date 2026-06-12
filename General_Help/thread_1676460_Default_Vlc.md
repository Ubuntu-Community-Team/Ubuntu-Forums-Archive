---
title: "Default Vlc"
date: 2011-01-27
forum: General Help
---

### Post by adeee on 2011-01-27
Guys i just listening a song on vlc and read  this thread.
[http://ubuntuforums.org/showthread.php?t=1666337](http://ubuntuforums.org/showthread.php?t=1666337)
After reading complete thread i just off vlc and then start installing software with instructions given in the thread. 
When google earth installed. i just use google earth only 10 minutes and then again play a song.

then vlc looks like this. 
[ATTACH]182073[/ATTACH]

and no video playing. no main menu show.
What it happen.?
i try to remove it.
sudo apt-get remove vlc
and again install it sudo apt-get install vlc

same result.
then i apply
sudo apt-get remove --purge vlc
and install again same result.

i just want to vlc its default condition.

---

### Post by TeoBigusGeekus on 2011-01-27
You have applied a skin to vlc.
Go to ~/.local/share/vlc/ and delete the skins2 folder.

---

### Post by adeee on 2011-01-27
> **TeoBigusGeekus said:**
> You have applied a skin to vlc.
Go to ~/.local/share/vlc/ and delete the skins2 folder.

its not there. in vlc folder i locate only this file.

ml.xspf

so any other  idea

---

### Post by TeoBigusGeekus on 2011-01-27
Ok, plan B.
Try to access the Tools menu from your current vlc status: click and/or right click everywhere until you find it. Once there, go to Interface and choose Use native style (instead of Use custom skin).

---

### Post by adeee on 2011-01-27
> **TeoBigusGeekus said:**
> Ok, plan B.
Try to access the Tools menu from your current vlc status: click and/or right click everywhere until you find it. Once there, go to Interface and choose Use native style (instead of Use custom skin).

i already tried this but its not done. even right click not works. can you tell me how to remove complete vlc. every file and directory of vlc even vlc configuration file too.
then i install it again.:(

---

### Post by TeoBigusGeekus on 2011-01-27
Have you tried looking in /usr/share/vlc for a skins2 folder?

---

### Post by adeee on 2011-01-27
> **TeoBigusGeekus said:**
> Have you tried looking in /usr/share/vlc for a skins2 folder?

nopsss what i need to do with this folder? delete it?

---

### Post by TeoBigusGeekus on 2011-01-27
Post us its contents.

---

### Post by adeee on 2011-01-27
here it is.
[ATTACH]182087[/ATTACH]

---

### Post by TeoBigusGeekus on 2011-01-27
It looks perfectly normal - same as mine.
Run out of ideas...
What I'd do:
```
sudo apt-get purge vlc
```
then 
```
find / -name vlc 2>/dev/null
```
to find any remnant of it in my system.
Delete whatever the find command comes up with and try to reinstall.

---

### Post by adeee on 2011-01-27
> **TeoBigusGeekus said:**
> It looks perfectly normal - same as mine.
Run out of ideas...
What I'd do:
```
sudo apt-get purge vlc
```then 
```
find / -name vlc 2>/dev/null
```to find any remnant of it in my system.
Delete whatever the find command comes up with and try to reinstall.


/usr/lib/vlc
/usr/bin/vlc
/usr/share/vlc
/usr/share/doc/vlc
/etc/vlc
/home/adeee/.cache/vlc
/home/adeee/.local/share/vlc
/home/adeee/.config/vlc


these files find command finds.
so you want me to delet these files?


ok buddy i remove all these files.
and reinstall it then this error occurs.:P
[ATTACH]182099[/ATTACH]

---

### Post by TeoBigusGeekus on 2011-01-27
For starters, purge vlc and delete the folders in your /home.
Reinstall; if the problem persists, purge again and delete all of them.

---

### Post by adeee on 2011-01-27
> **TeoBigusGeekus said:**
> For starters, purge vlc and delete the folders in your /home.
Reinstall; if the problem persists, purge again and delete all of them.

am not following you. what do you mean by purge? first time i hear this word.
please explain.

---

### Post by AlphaLexman on 2011-01-27
```
sudo apt-get remove *packagename*
``` will remove the program from your computer.
While,
```
sudo apt-get purge *packagename*
``` will remove the program and their configuration files from your computer.

---

### Post by TeoBigusGeekus on 2011-01-27
^This.

---

### Post by adeee on 2011-01-28
hay guys its the problem of  installing Google earth. i just delete the google earth and vlc works fine. can you see the code of this thread what mistake going on there? 
[http://ubuntuforums.org/showthread.php?t=1666337](http://ubuntuforums.org/showthread.php?t=1666337)

It effects many other application too. my Kpatience game also not running. and am sure other some application may effected.
can you provide good and complete without bug code?

---

