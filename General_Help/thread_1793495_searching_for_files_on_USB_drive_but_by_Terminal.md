---
title: "searching for files on USB drive but by Terminal"
date: 2011-06-29
forum: General Help
---

### Post by rreyes3713 on 2011-06-29
What folder[?] do I search to read for a USB drive (or any hard drive such as a partition)  through the terminal?

If you are asking why, I need to change the permission of this one folder. It was private, setting was 700 in UNIX I would like chmod to 755.

You see, I'm browsing my laptop's hard drive that's mounted on a docking bay SATA to USB and I can't seem to browse one of my user's and I recall the permission setting was 700.

... nope, using the "Property -> Permission" method did not work.

---

### Post by wolfen69 on 2011-06-29
Just do:
```
cd /media
```
then
```
ls
```
and you should see your usb drive listed.

---

### Post by guzjd on 2011-06-29
How about ?
```
find /media -name <filename>
```

---

### Post by rreyes3713 on 2011-06-29
Cool, thanks guys! :p  You guys are good.

Found my way!  Kind of fill silly asking such a fundamental question.

uh ... one more question, what is the UNIX command to change permission to the folder and all the sub-folder and files underneath it? I don't have my UNIX text book in front of me.

sudo -R chmod 755 *   [ then what? something or rather ]

---

### Post by smurphy_it on 2011-06-29
```
chmod -R 755 /folder_name_here
```

---

### Post by rreyes3713 on 2011-06-29
Thanks, that'll do it!

---

