---
title: "Can't compile &gt;:/"
date: 2011-06-30
forum: General Help
---

### Post by johndebian on 2011-06-30
ok i have this source: 

[ftp://ftp.snt.utwente.nl/pub/games/urbanterror/iourbanterror/source/complete/](ftp://ftp.snt.utwente.nl/pub/games/urbanterror/iourbanterror/source/complete/)

I'm trying to compile it so that there is a .i386 executable in the 
ioUrbanTerrorClientSource/build/release-linux-i386/ FOLDER

I open terminal and [cd ~/Desktop/ioUrbanTerrorClientSource] then [make -ik] but im not getting a .i386 executable.

My friend can compile this source with no problems, but i cant >:/

Maybe im missing something:(

---

### Post by dFlyer on 2011-07-01
Is build-essential installed?

---

### Post by Bachstelze on 2011-07-01
> **johndebian said:**
> 
I open terminal and [cd ~/Desktop/ioUrbanTerrorClientSource] then [make -ik] but im not getting a .i386 executable.


What are you getting instead?

---

### Post by johndebian on 2011-07-01
build-essential is already the newest version.

And its kind of compiling it but i'm not getting the .i386 like i should be getting. 

After it compiles i get a few folders.

---

### Post by Bachstelze on 2011-07-01
Paste the output (all of it!), there's probably something helpful in there.

---

### Post by dFlyer on 2011-07-01
You may be missing some dev lib. Post your output.

---

### Post by johndebian on 2011-07-01
Ok after you said i might be missing some dev lib, that is what i orignally thought. so i searched around and found this:

sudo apt-get install libsdl1.2-dev

and when i compiled [make -ik] I finally got a .i386 

Thank you so much!!

---

