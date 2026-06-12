---
title: "Access &quot;Program Files&quot; in .wine/drive_c with the terminal"
date: 2010-01-13
forum: General Help
---

### Post by ricardo.gloe on 2010-01-13
How do I access "Program Files" located in  ~/.wine/drive_c with the cd command ? when I try, this is what happens:

```
rrmendes Wed Jan 13 14:24:38 BRST 2010
[~]cd /home/rrmendes/.wine/drive_c/Program Files/Okapi/Olifant
bash: cd: /home/rrmendes/.wine/drive_c/Program: No such file or directory

rrmendes Wed Jan 13 14:24:38 BRST 2010
[~]

```            

any help would be appreciated, thanks

---

### Post by michy99 on 2010-01-13
The problem is the space in Program Files. You can use the backslash before the space```
cd /home/rrmendes/.wine/drive_c/Program\ Files/Okapi/Olifant
```or use quotation marks.```
cd /home/rrmendes/.wine/drive_c/"Program Files"/Okapi/Olifant
```

---

### Post by USB_NL on 2010-01-13
i think 
```
cd "/home/rrmendes/.wine/drive_c/Program Files/Okapi/Olifant"
```
will works also but i might be wrong maby you can test it ;)

---

