---
title: "Cannot mark .EXE file as executable in Natty Narwhal"
date: 2011-05-07
forum: General Help
---

### Post by aisajib on 2011-05-07
I installed Ubuntu Natty Narwhal and then installed Wine Windows Compatibility Layer through the Software Center. Now, I'm trying to install windows programs using Wine Layer. But as soon as I open a .exe file, an error message says the file isn't marked as executable. I then opened up the properties of the file and on the Permissions tab, I checked "Mark this file as executable" option. However, I noticed that the check vanishes within a second. I clicked and checked it several times and each time the check vanishes and remains not executable.

I tried this on several Windows applications (.exe file) and all of them had the same reaction. In Maverick, I had Wine installed and this problem never existed.

For the record, I tried the sudo nautilus way still no luck. Any help?

---

### Post by Finalfantasykid on 2011-05-07
that is strange.  What happens when you chmod +x the file?

```
chmod +x program.exe
```

---

### Post by SavageWolf on 2011-05-07
Are you running the programs from a NTFS/FAT filesystem (I.E. Windows ones), if so, you will have to move them on to your desktop (or somewhere else on your computer).

---

### Post by Morbius1 on 2011-05-07
As it turns out you don't have to mark it executable to run on Wine.  It's not Wine that's throwing the error it's something called  cautious-launcher. I'll give you 3 ways to circumvent the problem:

**[1] Run it from the terminal:**
```
wine "/path/to/exe/file"
```**[2] Fix the file association:**
Right click an *.exe file and select Properties -> Open With -> Add -> Use a custom command > type in: wine

In the "Open With" tab mark the "wine" [COLOR=Blue]**you added**[/COLOR] as the default ( from the Wine that's already selected) and every time you run an exe it should select the wine without the cautious launcher script.

**[3] Fix it at it's source:**
Open up as root "Properties" on /usr/share/applications/wine. 

What you will see is this:
>  cautious-launcher %f wine start /unix                                 Change it to this:
>  wine start /unix                                 I would go with option [2] myself. I don't like messing with system files unless I really have to.

---

### Post by supranov on 2011-07-22
Thanks, methods 2 works for me.. :D

---

### Post by arun sharma on 2011-11-15
Hi, i tried all these ways but none of this worked for me. i still have the same problem. as told in the last method, i tried to change **cautious-launcher %f wine start /unix** to **wine start /unix** but as soon as close it and reopen its not changed. it will still be **cautious-launcher %f wine start /unix**. i dint have this problem for about 3 months i am using this ubuntu version, but from few days i am seeing this.

---

### Post by Morbius1 on 2011-11-15
It sounds like you are not accessing the file in Nautilus as root:
```
gksu nautilus /usr/share/applications
```

---

### Post by arun sharma on 2011-11-19
Thanks a lot
 it worked for me...

---

