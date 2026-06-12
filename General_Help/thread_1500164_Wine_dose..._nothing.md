---
title: "Wine dose... nothing?"
date: 2010-06-02
forum: General Help
---

### Post by Neon_c on 2010-06-02
Ok what i'm trying to do is install WoW on my Ubuntu Studio box using Wine 1.0.1 . I can get the wine configuration and i can get notepad (both came with Wine). However i can not get it to execute the WoW installer.

this is what happens
```

neon@NeonStudio:/windows$ wine /windows/TryWoW.exe 
neon@NeonStudio:/windows$ 

```

it looks like wine exits without errors but dose nothing. Any ideas?

---

### Post by jerenept on 2010-06-02
You are already in the "windows" folder. If I am not mistaken, all you need to do is 
```
neon@NeonStudio:/windows$ wine TryWoW.exe 
```

---

### Post by jerenept on 2010-06-02
A newer version of wine may be in order too...;)

---

### Post by Neon_c on 2010-06-02
well it wont execute that way either. also 1.0.1 is the most up to date stable version of wine (ref wineHQ.org)

Well i tryed Wine with the start flag and it did something else
```

neon@NeonStudio:/windows$ wine start 'd:\TryWoW.exe'
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:exec:SHELL_execute flags ignored: 0x00000500

```
at this point ./windows/ is 'mounted' to d:\

---

