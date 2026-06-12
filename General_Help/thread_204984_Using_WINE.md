---
title: "Using WINE"
date: 2006-06-27
forum: General Help
---

### Post by bellaterror on 2006-06-27
Okay I understand that you have to put in the command in windows format and all to run the file you want unless you have in the windows\system32 area but where is that area?! I tried using winecfg to autodetect drives unable to define device name so anyone that is familiar with using this program I could really use some help thanks.

---

### Post by nixternal on 2006-06-27
/home/username/.wine/drive_c/windows/system32

---

### Post by bellaterror on 2006-06-27
okay so this is where i need to make this folder at? Because it doesn't exist....

---

### Post by nixternal on 2006-06-27
if you installed wine, and ran wine for the first time, it automatically creates the directory...it is created as a hidden directory within your home directory.

if you type
```
# wine
```
at the command line, what happens?  does wine try to run?

where did you install wine from?  did you install it from the Ubuntu Repositories?  i.e. installed it via Synaptics, Add Programs, Adept, or apt-get?

Are you getting errors upon running wine at all?  if so what are the errors?

What program are you trying to run with wine?  have you checked the wine database at their website to see if the program is supported?

if you can answer any of those questions, it will be greatly appreciated. good luck!!!

---

### Post by bellaterror on 2006-06-27
Well I put it in through synaptic first then did apt-get because it didnt seem to work but no I havnt checked the database do you have a link or anything to where I can see? but so if it's in its databse that's the only way it'll work? (when i type in wine it gives me the three help lines like its suppose to)

---

### Post by bellaterror on 2006-06-28
can anyone help with giving me a little insight on how this works

---

### Post by bellaterror on 2006-06-28
can anyone help with giving me a little insight on how this works

---

### Post by bellaterror on 2006-06-28
Okay I guess I'll go find out this stuff on my own =/

---

