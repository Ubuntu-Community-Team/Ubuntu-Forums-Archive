---
title: "Unable to run any programs using wine."
date: 2010-02-18
forum: General Help
---

### Post by karthick87 on 2010-02-18
I cant able to run any programs using wine.Wat may be the problem?How to solve this??

---

### Post by howefield on 2010-02-18
It may be that the program you are trying to run simply is not supported in Wine. Not all windows applications will work or work well through Wine.

What are you trying to run ?

---

### Post by karthick87 on 2010-02-18
None of the executable files are opening in wine..

---

### Post by Jackzor on 2010-02-18
What are some examples of things you are trying to run. 


Try reinstalling wine.

---

### Post by karthick87 on 2010-02-18
Photoshop,Microsoft Office etc etc..

---

### Post by Jackzor on 2010-02-18
Are they already installed or is that what you are trying to do?

(You could just use Gimp and OpenOffice.)

---

### Post by howefield on 2010-02-18
> **getyourkarthick said:**
> None of the executable files are opening in wine..

How are you trying to open them ?

Right click the windows executable and select "Open with Wine Windows Program Loader"

---

### Post by Jackzor on 2010-02-18
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

---

### Post by karthick87 on 2010-02-18
I remember that i have used some unlink command but i dont remember after that none of my programs are opening in WINE..

---

### Post by howefield on 2010-02-18
> **getyourkarthick said:**
> I remember that i have used some unlink command but i dont remember after that none of my programs are opening in WINE..

Ooops... :)

Was this a command in terminal ?

If so, open a terminal and using the up arrow, scroll back through the commands to (hopefully) find the one you are talking about.

Post it back here.

---

### Post by karthick87 on 2010-02-19
This is that command **unlink ~/.wine/dosdevices/z:**

---

### Post by karthick87 on 2010-02-21
Bump...

---

### Post by karthick87 on 2010-03-01
I have reinstalled wine..But still no use...I have executed this command [B]
"unlink ~/.wine/dosdevices/z:"  [/B]I have read this thread [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) and followed the instruction after that i am unable to run any programs using wine..Help me to solve this problem..

Thanks in advance...

---

### Post by karthick87 on 2010-03-02
I have solved this problem by removing .wine in the home folder and i have recreated it by executing winecfg from terminal..Thanks for your help so far..

---

