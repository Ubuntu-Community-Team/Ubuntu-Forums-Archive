---
title: "how to execute a .bin file"
date: 2010-05-18
forum: General Help
---

### Post by lory on 2010-05-18
can anybody help me to execute a .bin file. I have downloaded an application but I cannot run it (not recognized by double click).
thanks

---

### Post by WorMzy on 2010-05-18
Right click it, click "Properties", click "Permissions", check the box for "Allow executing file as a program".

---

### Post by Chesamo on 2010-05-18
```
$ sudo chmod +x file.bin
$ ./file.bin
```

---

### Post by doas777 on 2010-05-18
well, first off, there are several kinds of bin files, so what did you pull down? 

1) .bin as a disk image type 
2) .bin as an executable type
3) .bin as a non-executable binary resource file

second, you will almost never double click anything to run it in linux. you will often click launchers, to load apps, but you will basically never double click an executable. you either run it via a launcher, or use Alt+F2 and type in the name, or spawn it from the terminal.

most likely the answer to your question, is to open a terminal (applications-Accessories-terminal). 
```

cd <path to the folder that contains the bin file>
sh ./<file name.bin>

```
if you are installing software you may need to use 'sudo' when running the 'sh' line.

---

### Post by WorMzy on 2010-05-18
No need for the sudo for chmod, but I expect that you *will* need to use it to execute the .run file.

---

### Post by lory on 2010-05-18
> **Chesamo said:**
> ```
$ sudo chmod +x file.bin
$ ./file.bin
```


I moved the file to my desktop
file name is ptlx10.bin
I typed sudo chmod +x ptlx10.bin
answer: no such file or diredtory

---

### Post by doas777 on 2010-05-18
show us the output of 
```

ls -al <path to bin files parent folder>

```

---

### Post by eltonw on 2010-05-18
> **lory said:**
> I moved the file to my desktop
file name is ptlx10.bin
I typed sudo chmod +x ptlx10.bin
answer: no such file or diredtory

You need to be IN the directory where the file is located. An easy way to find out this is to type:
ls

this will LiSt the files in the current directory. Or else you would change to the directory, in this case: cd desktop OR cd Desktop (in LINUX folder / file names are CASE sensitive.

[FONT="Arial Black"]_THIS_ should also help to you to become more familiar with using LINUX:[/FONT]
[http://ubuntuforums.org/showthread.php?t=1483371]("http://ubuntuforums.org/showthread.php?t=1483371")

HTH...

---

