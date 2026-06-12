---
title: "Can't add fonts?"
date: 2006-04-23
forum: General Help
---

### Post by nismoskys on 2006-04-23
Whenever i try to add fonts into the "fonts:///" It doesnt work. i know i've done it before, and it worked then, but not anymore.

I open nautilus as root and then browse to "fonts:///" and just copy a .TTF font file and paste it into there, but it doesnt work. copying works, and in the fonts:/// folder, paste isnt greyed out or anything, but after i click paste, nothing happens, same for ctrl+c nd ctrl+v. i've done this a while ago and it worked fine but it's not working for some reason.

also tried using the mv command in the terminal, but it doesnt recognize fonts:/// as a directory.

anybody know why its not working, or some other way to get the fonts 'installed'.

---

### Post by htinn on 2006-04-23
Just open ~/.fonts and copy ttf files there (create the folder if necessary).

---

### Post by nismoskys on 2006-04-23
**perfect**

thank you very much :)

---

