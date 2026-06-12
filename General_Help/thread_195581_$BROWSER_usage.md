---
title: "$BROWSER usage?"
date: 2006-06-13
forum: General Help
---

### Post by _simon_ on 2006-06-13
How do I set this?

How do I see what is currently set?

(Google Earth uses this to open the browser, currently it's opening Firefox when I want it to open Swiftfox)

---

### Post by oscar on 2006-06-13
have you tried changing your preferred web browser in System > Preferences > Preferred Applications ?

---

### Post by _simon_ on 2006-06-13
Yeah it works fine doing it that way for any other program but not for Google Earth.

The Google Earth readme says it relies on the $BROWSER setting.

---

### Post by Rui Pais on 2006-06-13
Hi,
try to set it at .bashrc:
```
export BROWSER=/my/path/to/swiftfox
```
then do 
```
source .bashrc
```
and check it with
```
echo $BROWSER
```

---

### Post by _simon_ on 2006-06-13
where should .bashrc be located?

I have found bash.bashrc in  /etc and dot.bashrc in /usr/share/base-files 

I don't think either of those are correct?

---

### Post by Rui Pais on 2006-06-13
Hi,
simply edit the .bashrc on your home folder (~/.bashrc)
If you don't have one just make it. 
You sould have one with your bash definitions like colour output, prompt definitions, alias and stuff like that.

---

### Post by _simon_ on 2006-06-13
Sometimes I can be so stupid.

I was looking at the hidden folders in /home and not seeing it, then I realised it wasn't a folder!

Thank you very much, it's worked perfectly :)

---

### Post by Rui Pais on 2006-06-13
no problem :)

---

