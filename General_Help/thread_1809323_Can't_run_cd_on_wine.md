---
title: "Can't run cd on wine"
date: 2011-07-21
forum: General Help
---

### Post by fredca on 2011-07-21
I'm using Wine, and I'm trying to open a executable file that's in a CD.
I already autodetected all my drivers, I've configured the media driver (where the CD is located), and everytime I try double-clicking the file it just gives me this error-message.

> The file '/media/SR-Codigo-CD1/TesteExame.exe' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the executable bit.

Any help will be appreciated.

---

### Post by mc4man on 2011-07-21
right click on the .exe > open with - other application > use a custom command
For the command simply use
wine
In the future "wine" will be a r. click option, use it instead of 'wine windows program loader'

---

### Post by Nytram on 2011-07-21
Another option would be to type this command into a terminal:

> wine /media/SR-Codigo-CD1/TesteExame.exe

---

