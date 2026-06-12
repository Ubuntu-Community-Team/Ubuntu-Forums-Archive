---
title: "Wine , not a problem, just need some info"
date: 2006-05-28
forum: General Help
---

### Post by cobbweb on 2006-05-28
Hey, 
  I used wine to install Photo Shop on my computer but I don't know how I can now access Photoshop. There is no link anywhere, and  I don't know where to look for one . Anyone know how to open my Photoshop program??? 

 Also, I need to somehow update wine and then upgrade, because every time i try to do a normal sodu apt-get update && upgrade I get something that tells me that i need to do wine sepratly. Not sure how to do that but would like to know if anyone else does. Thanks 

Cobbweb

---

### Post by Sutekh on 2006-05-28
Where is Photoshop installed?

It would be something like this
```
wine ~/.wine/drice_c/Program\ Files/Photoshop/Photoshop.exe
```
You will need to chech the path of the .exe.  When you know you can use this command to make a launcher.
[quote=cobbweb]Also, I need to somehow update wine and then upgrade, because every time i try to do a normal sodu apt-get update && upgrade I get something that tells me that i need to do wine sepratly.[/quote]
Probably because the wine package asks for confirmation as it is not authenticated, but I'm not really sure I know what you mean.

---

### Post by simo on 2006-05-28
Look in your home directory for .wine.
For example if your home directory is
/home/john

do

cd /home/john/.wine 

then do ls and you should see directory named drive_c

Directory named drive_c represents partition where windows are installed.
Inside drive_c are folders named My Documents,Program Files ...

So look in Program Files for your program.

Hope it helps....

---

