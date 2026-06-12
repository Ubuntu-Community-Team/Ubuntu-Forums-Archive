---
title: "Mysterious problem"
date: 2011-08-06
forum: General Help
---

### Post by Carborundum on 2011-08-06
I recently installed Heroes of Might and Magic III through wine. It works perfectly, but I encountered a strange problem when I tried to create a launcher on my desktop:

Launching the game from the directory where it is installed works just fine:
```
alexander@alex-netbook:~/.wine/drive_c/Program Files/GOG.com/Heroes of Might and Magic 3 Complete$ wine Heroes3.exe
```But launching it from anywhere else causes wine to give me an error message. This, for example, does not work:
```
alexander@alex-netbook:~$ wine ".wine/drive_c/Program Files/GOG.com/Heroes of Might and Magic 3 Complete/Heroes3.exe"
```The error messsage is "Files from Heroes III are missing. Please reinstall Heroes III."

Any ideas as to why this happens?

---

### Post by decrepit on 2011-08-06
> **Carborundum said:**
> >>>>>
```
>>>>>>/GOG.com/Heroes of Might and Magic 3 Complete$ wine Heroes3.exe
``` >>>>>>
```
>>>>>>>>/GOG.com/Heroes of Might and Magic 3 Complete/Heroes3.exe"
```The error messsage is "Files from Heroes III are missing. Please reinstall Heroes III."

Any ideas as to why this happens?

Maybe the difference in the 2 line endings?

---

### Post by SavageWolf on 2011-08-06
I suspect that the game uses relative paths (It will only look in the current folder or ones "next" to it).

If you want to run it from anywhere, it's just a simple task of putting the following in a shell file (Create a blank file, make it executable, paste this into it).

```

#!/bin/bash
cd /home/alex/.wine/drive_c/Program\ Files/GOG.com/Heroes\ of\ Might\ and\ Magic\ 3\ Complete/;
wine Heroes3.exe;

```

---

### Post by Carborundum on 2011-08-06
> **SavageWolf said:**
> I suspect that the game uses relative paths (It will only look in the current folder or ones "next" to it).

If you want to run it from anywhere, it's just a simple task of putting the following in a shell file (Create a blank file, make it executable, paste this into it).

```

#!/bin/bash
cd /home/alex/.wine/drive_c/Program\ Files/GOG.com/Heroes\ of\ Might\ and\ Magic\ 3\ Complete/;
wine Heroes3.exe;

```
Thank you!

---

