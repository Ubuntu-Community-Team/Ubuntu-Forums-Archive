---
title: "How to disable wine temporarily?"
date: 2010-02-06
forum: General Help
---

### Post by karthick87 on 2010-02-06
I like to disable wine temporarily?How to do this?

---

### Post by karthick87 on 2010-02-07
Bump...

---

### Post by Bachstelze on 2010-02-07
What do you mean, disable WINE? WINE is not a daemon.

---

### Post by 23dornot23d on 2010-02-07
Just remove it and add it back again .... after you have done whatever you want to do .......

sudo apt-get remove wine

sudo apt-get install wine

or do it in Synaptic package installer ...

Not sure why you want to disable it ..... but this will be reasonably quick and easy .....

and you will know that wine is not interfering with anything else, if that is the problem ?

---

### Post by jepjava on 2011-08-29
is it safe for the executable exe viruses if i dont disable wine?

---

### Post by 3Miro on 2011-08-29
Most viruses don't affect wine, however, it is theoretically possible for a virus to use wine and do damage.

Simply having wine installed will not execute anything from an .exe file. If you change the default program opening .exe files and you don't explicitly say "run with wine" you should be safe. To change the default program, right-click on the .exe file and select Properties, then change the "open with" to something other than wine.

---

