---
title: "running program in terminal without typing full path"
date: 2009-07-14
forum: General Help
---

### Post by Ajat on 2009-07-14
I installed sage.. by using ```
apt-get install sagemath
```
the program runs very well, by just typing ```
sage
``` in the terminal.
The problem is it gives me the old version.

So i go to the sage official website and download the latest version. They give me tar.gz file, which mean i just need to extract it and run it from it's directory.

Well, you know it's sometime irritating for me, to type the full path just to run the program.
It's a slow-down. 

Any advices to make an "informally installed" program recognized by the terminal?

i've tried to move the program folder to usr/local/bin..but still i can't make the terminal recognize this program. 

Thanks.

---

### Post by jerome1232 on 2009-07-14
Move the program to /usr/local, and create a symlink to the executable in /usr/local/bin, you may want to remove the old version via apt get.


if the binary is called 'sage' making a symlink would be done like this:
```
sudo ln -s /usr/local/PROGRAMFOLDER/sage /usr/local/bin/sage
```

---

