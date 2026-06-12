---
title: "Help with running 'unmarked .exe's'"
date: 2010-05-11
forum: General Help
---

### Post by thememan on 2010-05-11
I try to install some things with wine and i get a security message :

The file '/home/cale/Desktop/total-video-converter.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Help is appreciated. 

Cheers

---

### Post by lisati on 2010-05-11
.exe files are usually MS-DOS/Windows files. Are you using [Wine]("https://help.ubuntu.com/community/Wine")?

---

### Post by matchu on 2010-05-11
Hey there!

Files in a Linux system have permissions attached to them: who can read it, who can write it, and who can execute it. You need to give execution permissions for this file before you can run it.

Right-click the file, and choose Properties. Under the Permissions tab, ensure that the "Allow executing file as a program" box is checked, and see if that solves the problem.

Hope this helps!

---

### Post by ubunterooster on 2010-05-11
right-click on the .exe and select "properties">"permissions" and be sure "executable" is checked

---

### Post by thememan on 2010-05-11
Yes. It just wont let me run them. You know anything??

---

### Post by thememan on 2010-05-11
Ahhh thanks all for help. Ino it could be obvious but im only 14, I know quite abit tho

Cheers

---

### Post by doas777 on 2010-05-11
do you have wine installed ?
you cannot run an exe without wine.

to invoke them, use:
```
 wine <path to exe>
```

---

### Post by matchu on 2010-05-11
Since he mentioned WINE in the very first post, I assumed that he must be using WINE correctly - though since I don't use it often, it could very well be that the executable bit isn't required when running things with WINE. I wouldn't know xD

---

### Post by lisati on 2010-05-11
> **matchu said:**
> Since he mentioned WINE in the very first post, I assumed that he must be using WINE correctly - though since I don't use it often, it could very well be that the executable bit isn't required when running things with WINE. I wouldn't know xD

Missed that the first time I read the question. I don't use wine much either, and wasn't aware of a need to set the executable bit as well.

---

### Post by doas777 on 2010-05-11
so far as i'm aware, you don't need to set the x bit, since the actual binary is not executing in the traditional sense. it shoudl be wine itself that needs the x bit.

---

### Post by ubunterooster on 2010-05-11
If you don't have a .exe listed as "executeable" Wine will likely not be told to open them. This is usually an issue with a .exe file used to install the program, as Wine would have a menu entry once the program was installed, thus bypassing the need to click the .exe

---

