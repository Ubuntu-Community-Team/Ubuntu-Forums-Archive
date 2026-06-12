---
title: "Executables - No such file or directory"
date: 2010-06-06
forum: General Help
---

### Post by rdunnion on 2010-06-06
I have found when I try to execute certain executables that I am getting the error "No such file or directory." The file is obviously there I can see it's permissions but when I try to run it I get these errors. Does anyone know why this happens? Maybe it has something to do with the file being 32-bit and I am running Lucid x64?

---

### Post by Nate Richards on 2010-06-06
please use 84 -bit for this

---

### Post by rdunnion on 2010-06-06
The 64-bit forum has been closed to new posts and support is being handled in General Help.
[http://ubuntuforums.org/announcement.php?f=343]("http://ubuntuforums.org/announcement.php?f=343")

---

### Post by warfacegod on 2010-06-06
Try opening the files Properties> Permissions tab> and make Owner read/write/execute.

---

### Post by rdunnion on 2010-06-06
Permissions are set at 755, so there shouldn't be a problem. The box to allow this file to be executed is checked under properties.

---

### Post by WorMzy on 2010-06-06
Could you try running something again, then running ls, then copy-paste the contents of the terminal here so we can look at it and see if we can spot anything?

---

### Post by Leppie on 2010-06-06
how are you trying to launch these executables?

---

### Post by rdunnion on 2010-06-06
The file I'm trying to run is eschalon_book_2. I've tried it normally and with sudo as seen below.


ryan@ryan-desktop:~/bin/eschalon_book_2_1.03$ sudo ./eschalon_book_2
sudo: unable to execute ./eschalon_book_2: No such file or directory
ryan@ryan-desktop:~/bin/eschalon_book_2_1.03$ ls -l
total 283780

-rwxr-xr-x 1 ryan ryan   2414516 2010-05-27 15:49 eschalon_book_2

ryan@ryan-desktop:~/bin/eschalon_book_2_1.03$

---

### Post by oldos2er on 2010-06-06
```
sudo apt-get install ia32-libs
``` should allow you to run 32-bit executables.

---

### Post by WorMzy on 2010-06-06
My first thought is that root isn't able to access your home folder for some reason; so can you open nautilus as root (Alt+F2, then "gksu nautilus" [no quotes]) and see if you can manually navigate to the directory in question.

If you can, then try running the program with a full directory path (sudo /home/ryan/bin/eschalon_book_2_1.03/eschalon_book_2)

My second thought is that maybe that application isn't an application after all, but then it'd just either silently exit, or post an error.

Can you post the output of ```
file eschalon_book_2
```

---

### Post by rdunnion on 2010-06-06
@oldos2er - Yes! That was the exact thing I needed and in turn solved my printer driver issue as well. Thank you so much!

---

### Post by oldos2er on 2010-06-06
You're welcome!

---

