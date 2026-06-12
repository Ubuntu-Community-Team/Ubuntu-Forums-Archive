---
title: "wine"
date: 2009-11-29
forum: General Help
---

### Post by Mr Nemo on 2009-11-29
I am trying to make a launcher that will launch a windows application in wine. Any way to do this? I can't figure it out. The .exe is in my downloads file.

---

### Post by Virtual Liberty on 2009-11-29
```
wine /home/user/Downloads/application.exe
```

---

### Post by fluffman86 on 2009-11-29
Create your launcher, call it what you want, and in the "command" field, type:

wine %u /home/user/Downloads/windows\ program.exe

the \ character escapes any spaces or special characters.

and in my experience, you have to add the %u to launchers for some reason.  I just tested without it and it doesn't work.  :\

---

### Post by Mr Nemo on 2009-11-29
fluffman, I see you around all the time. Thanks for all your help. Thanks to you too liberty. Both of these ways seem to work.

---

