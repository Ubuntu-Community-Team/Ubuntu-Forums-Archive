---
title: "&quot;æøå&quot; in aMSN"
date: 2011-03-09
forum: General Help
---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-09
i have norwegian keyboard and normaly in the aMSN the letters "æøå" is not working
i have to type ```
LANG="nb_NO.UTF-8" amsn

```in terminal, then opens a new aMSN window, and then the "æøå" letters works, but if i try to close the terminal while in aMSN it says > A prosses is still running, if you close this window it will terminate and if i try to open aMSN after without typing this command first it doesent work with the letters "æøå".....
is there any way to fix it permantly so i can be able to use these letters automaticly without having to type the command every time?
sorry my english....

---

### Post by Perfect Storm on 2011-03-09
Edit the launcher in Applications tab. Right click ---> edit menu.

Find amsn and in its commando box you can fill out your custom command.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-09
Applications tab? where is it located?

---

### Post by Perfect Storm on 2011-03-09
upper left.

In english:
Applications | places | System |

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-09
oh ok i found it out.. now how do i make my own commands? i am not very mutch known with linux
since you are from denmark you must have these letters too no?
please tell me how do it

---

### Post by Perfect Storm on 2011-03-09
Have you found amsn in the menu editor?

click on it and click "edit".

A new window will pop up. In that window there should be a box called "command".

delete what's already written in there. And put this command into it instead:

LANG="nb_NO.UTF-8" amsn

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-09
it dos not work.. i get error that say something like
Could not start aMSN.
> wrong under opening of underproses
LANG="nb_NO.UTF-8" amsn (no such file or filecataloge)

---

### Post by Perfect Storm on 2011-03-09
okay, try this instead:

```
sh -c "LANG="nb_NO.UTF-8" amsn"
```

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-09
Worked! thanks:P

---

