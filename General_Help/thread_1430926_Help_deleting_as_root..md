---
title: "Help deleting as root."
date: 2010-03-15
forum: General Help
---

### Post by StruckByRain on 2010-03-15
[COLOR="Teal"]**There are these two files on my desktop that alien made when I was trying to get my ATI gfx card to work on my pc. I did get it to work, but now I can't delete these two folders from my desktop. It says Permission Denied. It states that the owner is root. I tried cd ~/Desktop then ls and then rm "file name" but it keeps saying is a directory. Please help! Thanks. =)**[/COLOR]

---

### Post by n0dix on 2010-03-15
Did you try with: sudo rm -r file_name

---

### Post by StruckByRain on 2010-03-16
[COLOR="Teal"]**No, but I will gladly try it now. =) I'm new to this whole linux ubuntu thing.... XP**[/COLOR]

---

### Post by soltanis on 2010-03-16
To remove a directory and all its contents, the general command is

```

rm -rf

```

Where -r means recursive, invoking rm on all a directory's contents and then the -f flag means force, i.e. don't ask for each file.

**Use this with caution**. I hope I need not tell you that doing this on something you want to keep will result in some serious issues. There is no Trash on the command line (well there is but it's a directory you move files into, rm doesn't use it). The only way to undelete something after this kind of atrocity is with a specialized program that examines your disk surface for the shards of the former file.

Running this command as root is...well, only called for in special circumstances.

So be careful.

Seriously. Careful. (I am pretty sure this is cited under malicious commands mostly because it is so easy to mess this up.)

---

### Post by StruckByRain on 2010-03-16
[COLOR="Teal"]**sudo rm -r file_name worked perfectly. Thanks. =)**[/COLOR]

---

### Post by n0dix on 2010-03-16
Please, add the Solved tag to the title.

---

