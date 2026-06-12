---
title: "Wine and Warcraft 3 error when patching: File not found"
date: 2010-09-07
forum: General Help
---

### Post by octohedra on 2010-09-07
Hello,

This is one of the only games i play, and it works perfect, but i have to patch it to play online, the thing is i get the following error when trying to apply the patch:

> Blizzard PrePatch v2.70 compiled on Jul  7 2003
This program patches Warcraft 3

Log created at 11:52 am on 09/07/2010

Registry error loading key 'Warcraft III\InstallPath'
File not found


RESULT: Prepatch failed
I tried editing the reg key:
```
gksudo wine regedit
```then went to:
HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft iii
and created a new String value: "Installpath"= C:\Warcraft III (my warcraft install path, inside c_drive folder)
Also tried other values, for example: /home/user/.wine/c_drive/warcraft III
Didnt work either.
Tried some other things and stil the same...

What could be the problem?
I've read that if you run warcraft it should create the reg key "blizzard entertaninment" but it didnt, i had to create it myself... maybe its not even reading the registry? :p

Maybe this problem can be solved by re-installing the game, but i copied it from my older machine, i dont have the cd's anymore...
Thanks for the help!

---

### Post by octohedra on 2010-09-07
okey, dumb me creating this topic before tryin to fix it with w3 fixer, anyways, if anyone has this problem, just google "w3 fixer". That'll fix it..


):P

---

