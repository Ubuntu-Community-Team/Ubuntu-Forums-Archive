---
title: "Creating a main menu command that performs two processes"
date: 2010-10-07
forum: General Help
---

### Post by kolo-01 on 2010-10-07
this should be quite an easy one for anyone who knows- i am trying to create an icon in the main menu that first kills an application and then opens another, i am able to perform the commands separately in the command, but can't work out how to execute them both in the same main menu command, maybe there is something to write in-between the commands, or is this process not possible?

---

### Post by Rinzwind on 2010-10-07
should be something like:
command1 && command2

---

### Post by kolo-01 on 2010-10-07
> **Rinzwind said:**
> should be something like:
command1 && command2

the double && is not working for me, it is only the first command that works, the second is ignored, thanks for the quick response

---

### Post by Rinzwind on 2010-10-07
Ok then I would suggest putting the 2 lines in  a file, make the file executable and add file to the menu item :)

---

### Post by Toz on 2010-10-07
Double && should work. Any chance you could show us the code you are trying to execute? Might make it easier to troubleshoot with the lights on.....

---

### Post by kolo-01 on 2010-10-07
> **Toz said:**
> Double && should work. Any chance you could show us the code you are trying to execute? Might make it easier to troubleshoot with the lights on.....

ok so this is the line i have copied into the command line of a  menu item
" wineserver -k && env WINEPREFIX="/home/kolo-01/.wine" wine "C:\full tilt poker\FullTiltPoker.exe" " they both work in separate individual commands, but this command is just killing the wineserver,.

basically the wineserver needs to be killed before the other process starts, i was thinking that maybe if they started at the same time the wineserver killing might kill the other process as it starts, but i tried the && with two separate program starters and only the first one ever starts, so im not sure what im doing wrong there?

---

