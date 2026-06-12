---
title: "need help with playing tf2."
date: 2012-01-06
forum: General Help
---

### Post by ugotboxed on 2012-01-06
i downloaded wine and i installed steam. when i finished downloading tf2 i tried to play it. it said "preparing for launch" like it normally does and then nothing happed. how do i fix this?

---

### Post by carl4926 on 2012-01-06
Did you check in here
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9901](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9901)

---

### Post by ugotboxed on 2012-01-06
That didn't work... unless i did something wrong. any other ideas?

---

### Post by topsites on 2012-01-06
Team Fortress 2 is a Windows application, Ubuntu is a Linux operating system.
There are no guarantees beyond that, Wine may or may not run it, this isn't Microsoft's world anymore.

---

### Post by carl4926 on 2012-01-06
> **ugotboxed said:**
> That didn't work... unless i did something wrong. any other ideas?

Not really
I had to google to find out what on earth tf2 was.

Go to .wine
Find the applications installation location, where the .exe is
open a terminal and start the application from the termina

```
wine ./applicationname.exe
```

see if there is any feedback from the terminal

---

### Post by raja.genupula on 2012-01-06
[http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/](http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9901](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9901)


Look at them

---

### Post by lite1979 on 2012-03-08
Applications>Wine>Configure Wine>Libraries tab

type gameoverlayrenderer.dll in the box, click "add" then disable it. Post your results.

---

