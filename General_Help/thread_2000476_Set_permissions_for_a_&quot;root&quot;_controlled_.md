---
title: "Set permissions for a &quot;root&quot; controlled folder."
date: 2012-06-09
forum: General Help
---

### Post by Beatsleigher on 2012-06-09
Hey guys!

As I mentioned, in one of my threads, I'm an Android dev, know my way around Windows, Android but still quite new to the Ubuntu interface...

I downloaded the source code of Android, it's in my home folder, and it's controlled by root, for some reason. I know I can change this in Terminal, but can someone tell me the rest? All I'm 100% sure about is ```
sudp -i
chmod
```And that's all I'm sure about. Yes, I do know, that I can use ```
sudo chmod
```

LG Simon

EDIT: The folder path is: /home/simon/WORKING_DIRECTORY

---

### Post by MG&amp;TL on 2012-06-09
```
sudo chown -R $USER:$USER ~/WORKING_DIRECTORY
```should work.

---

### Post by black veils on 2012-06-12
```
sudo chmod 777 -R /home/simon/WORKING_DIRECTORY
```will give all permissions read and write access, you should later be able to edit this within nautilus, by right-clicking directory or file and go to **properties** etc or continue using the command line method:

first number is Owner
second number is Group
third number is anyone else

 0 &#8211; no permission, this person cannot read, write or execute
    1 &#8211; execute only
    2 &#8211; write only
    3 &#8211; execute and write only (1 + 2)
    4 &#8211; read only
    5 &#8211; execute and read only (1 + 4)
    6 &#8211; write and read only (2 + 4)
    7 &#8211; execute, write and read (1 + 2 + 3)
   -R - means to all folders and files within

---

### Post by Morbius1 on 2012-06-12
The only problem with a "chmod 777 -R" is that the octal mode isn't smart enough to differentiate between a folder and a file so you end up with all files being executable.

If you do it this way:
```
 sudo chmod -R a+rwX  /home/simon/WORKING_DIRECTORY
```Then all Folders will be 777 and all files will be 666 unless the file was executable to begin with - that's what the big "X" does.

---

