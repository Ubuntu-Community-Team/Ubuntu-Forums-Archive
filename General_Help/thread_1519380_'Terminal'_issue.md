---
title: "'Terminal' issue"
date: 2010-06-28
forum: General Help
---

### Post by arijitm on 2010-06-28
Hi Guyz,

      i am recently downloaded and installed Ubuntu 10 on my Dell Inspirion 1525 laptop. 

      i now downloaded some software i need for my work and as default settings r unchanged the y downloaded in the Downloads folder. Now i cannot access the folder and thus the file in it using Terminal. 

      these r the steps i did: 

      [COLOR="Red"]cd /[/COLOR]
      [COLOR="Red"]cd home/arijitm [/COLOR] (<- arijitm is the user)
      now whhen i do [COLOR="Red"]'ls'[/COLOR] the [COLOR="Red"]'Downloads'[/COLOR] folder is showing
      but when i enter [COLOR="Red"]'cd downloads'[/COLOR] it says [COLOR="Red"]'bash: cd: downloads: No such file or directory'[/COLOR]

      Help Guyz!!!!

---

### Post by lisati on 2010-06-28
In linux, folder and file names are case-sensitive - "downaloads" is NOT the same as "Downloads".
Try:
```
cd Downloads
```

---

### Post by arijitm on 2010-06-28
did that, still the same.

---

### Post by Bucky Ball on 2010-06-28
Are you in the correct directory? The directory where 'downloads' directory is? If not you need to get there.

Yes, silly question perhaps, but you never know.

---

### Post by howefield on 2010-06-28
Can you post a print screen of your terminal ?

Alt + Printscreen to take a shot of the terminal.

---

### Post by yeleek on 2010-06-28
```
cd ~/Downloads
```

---

### Post by arijitm on 2010-06-28
thanks a heaven "**[COLOR="Blue"]yeleek[/COLOR]**" 
 "~/Downloads" worked.. 
.
 n thanks a lot to all of u guyz..

---

