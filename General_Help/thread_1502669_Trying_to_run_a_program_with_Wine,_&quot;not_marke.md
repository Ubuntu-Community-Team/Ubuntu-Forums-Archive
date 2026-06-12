---
title: "Trying to run a program with Wine, &quot;not marked as executable&quot;"
date: 2010-06-05
forum: General Help
---

### Post by Kael Seoras on 2010-06-05
I read somewhere that when this error happens, I need to go to the properties of the file, then permissions, then click "Allow executing file as a program." I tried this and got the error message: "The permissions could not be changed. Sorry, could not change the permissions of 'AUTORUN.EXE': Error setting permissions: Read-only file system" Is there anything I can do about this? Or should I be glad I did dual-boot and run Windows programs on Windows? :lol:

---

### Post by Vaphell on 2010-06-05
that autorun.exe is on cd/dvd? what happens when you try **wine /path/to/autorun.exe** from command line?

---

### Post by Kael Seoras on 2010-06-05
> kelly@kelly-laptop:~$ wine /path/to/autorun.exe
wine: cannot find '/path/to/autorun.exe'
kelly@kelly-laptop:~$ wine /path/to/RA1/autorun.exe
wine: cannot find '/path/to/RA1/autorun.exe'
kelly@kelly-laptop:~$ wine /RA1/autorun.exe
wine: cannot find '/RA1/autorun.exe'
kelly@kelly-laptop:~$ wine /autorun.exe
wine: cannot find '/autorun.exe'
I played around, had no luck...I'm sure I'm doing it horribly wrong :lol: I am definitely a linux noob.

It is on a CD...the game Red Alert 2, to be specific. I wanted to try installing it.

---

### Post by jerome1232 on 2010-06-05
When he said /path/to/autorun.exe he meant to put in the real path. which is probably

```
wine /media/cdrom/autorun.exe
```

If that's not it then with the cd inserted post the output of the following command so we can help you figure out the path.

```
ls /media
```

---

### Post by Kael Seoras on 2010-06-06
That's what I was going for with my later attempts...wasn't sure what names to use...

Well, here's what happened with both those things:
> kelly@kelly-laptop:~$ wine /media/cdrom/autorun.exe
wine: cannot find '/media/cdrom/autorun.exe'
kelly@kelly-laptop:~$ ls /media
RA1

---

### Post by jerome1232 on 2010-06-06
So it's probably

```
wine /media/RA1/autorun.exe
```

You know what might be easier, open a terminal and just type wine with a space after it, then drag the .exe into your terminal and press enter.

---

### Post by dtfinch on 2010-06-06
and you might need to type autorun.exe as all caps.

---

### Post by Kael Seoras on 2010-06-06
SWEET. That did it. Thanks :D

---

### Post by twm3 on 2011-07-24
Hi All,

Not to put to fine a point on it but being a relative Linux newb and always forgetting where my CD/DVD is mounted, I realized that the error message was giving me a big clue to what I should be doing.

When I clicked on Setup.exe, I received the error message:
[INDENT]The file '/media/TOPOUS2008/Setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
[/INDENT]The error message was giving me the exact file that was creating the problems so from the command line, I typed:
[INDENT][FONT=Courier New]wine /media/TOPOUS2008/Setup.exe[/FONT]
[/INDENT]which worked like a champ.

Thanks to all the above that gave hints to what needed to be done.

~Tom

---

