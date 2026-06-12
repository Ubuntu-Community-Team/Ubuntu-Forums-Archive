---
title: "What is the wine command for wine program launcher?"
date: 2010-10-26
forum: General Help
---

### Post by X-Windows on 2010-10-26
I'm trying to set up a launcher for an installed wine program and cant get the commands to work right. The program launches fine if I open it with &quot;Wine Program Loader&quot; but not if I use the command wine &quot;...&quot; from anywhere but the local directory. If I open a terminal and cd to the directory containing the .exe and run &quot;wine Program.exe&quot; it opens fine, but running wine &quot;Folder/Program.exe&quot; doesn't work.  I'm sure there is a command I'm missing somewhere that runs the &quot;wine&quot; command from the target directory, I just can't figure out what it is. Any help would be appreciated as I'm prety stuck here...  If possible could you provide a basic example, just saying "use winecmd to run it" doesn't help much as syntax is quite important.

---

### Post by papibe on 2010-10-26
I'm a little confused with the notation you're using. It would be very helpful if you post examples of what you're doing.

For example, I use a windows bencode editor like this:
```
$ wine BEncode\ Editor.exe
```
or
```
$ wine "BEncode Editor.exe"
```

Did that help?
Regards.

---

### Post by X-Windows on 2010-10-26
Sorry I'll try to clarify.  I have a wine program installed. This program launches correctly if I set the "Open With" to "Wine Windows Program Loader" and double click the exe. However when I try to add this program to the menu I dont know what to put in the "command" box. I tried both of these to no avail:  

```
wine "~/.wine/drive_c/Program/Program.exe"
```
```
wine "C:\Program\Program.exe"
```

I'm pretty sure there was some way to run the wine program launcher so that it ran inside the directory containing the target exe.

Basicly I dont know what the command is to run the Wine Windows Program Loader... That should be able to be input into the "command" box in the launcher with little trouble.

---

### Post by papibe on 2010-10-26
WOW! that is very interesting, as I change my command for a one using the user shortcut "~/..."  IT DOES NOT WORK!!

I'm pretty sure if you use this in the command, it will work:
```
wine "/home/youruser/.wine/drive_c/Program/Program.exe"
```
change "youruser" for your actual username (I am assuming  /home/youruser/ is your home directory here).
Even this will work too:
```
"/home/youruser/.wine/drive_c/Program/Program.exe"
```

Good Luck!

---

### Post by mc4man on 2010-10-27
If for some reason you wished to use ~/ instead of /home/username/ect,ect then you need to move your ' or " inside of ~/

---

### Post by X-Windows on 2010-10-27
Tried the command **wine "/home/username/.wine/Program/Program.exe"** and it executed the program with the same error as when I cd to one directory higher than the exe file then run **wine "Program/Program.exe"**. 

Very strange how it works if I use terminal and cd to the directory containing the exe then run **wine Program.exe**... Is there something with the **wine** command that checks what directory it is in?

---

### Post by X-Windows on 2010-10-27
*bump

---

### Post by papibe on 2010-10-27
Did you try this just the path (works for me):
```
"/home/youruser/.wine/drive_c/Program Files/Program.exe"
```
Note that this time I used "Program Files"... just in case.

Regards.

---

