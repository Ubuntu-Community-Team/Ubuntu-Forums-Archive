---
title: "Error: dependency resolution failed - kpackagekit !"
date: 2009-12-08
forum: General Help
---

### Post by pirlo89 on 2009-12-08
hello !

i have been having a problem with this messages showing up every now and then, it says :

( A package dependency could not be found.
More information is available in the detailed report.
>>There are broken dependecies on your system. Please use an advanced package manage e.g. Synaptic or aptitude to resolve this situation. )

and since im a newbie i dont know how to install synaptic on kubuntu which im using now.:(

please help as soon as you see this :-(

Note: i think this problem has started after i installed frostwire.

---

### Post by karlmp on 2009-12-08
go to a terminal and type:
```
sudo aptitude
```

then type your password and press enter

---

### Post by pirlo89 on 2009-12-08
ok, then what ?

i looked for frostwire in there and it appears to be marked in red, it says :

( some dependencies of frostwire are not satisfied : frostwire depends on sun-java6-jre [multiverse] )

so i guess the problem is with java6 , how do i uninstall it and then reinstall it again , or should i just uninstall frostwire (which i dont really need right now)

plz help :sad:

---

### Post by pirlo89 on 2009-12-09
[SIZE="5"]problemo solved!

i opened my terminal>> went to root >> reinstalled java.

anyway, thanks for helping.
[/SIZE]
( with every problem that i fix in linux i fall more in love with it , isnt that twisted ? :-k , it used to be the other way around in windows )

---

### Post by polo86 on 2010-02-09
hi,

i'm a new user of kubuntu. 
I tried to install : sudo apt-get install openjdk-6-jre 
because i need it for eclipse in python but now kpackake kit doesn't work.
I tried this but it doesn't word : sudo apt-get remove --purge openjd-6-jre   
so could you explain me how i have to do

sorry for my english and thanks for your advices

---

### Post by polo86 on 2010-02-09
i tried alone with the command 
sudo apt-get install -f

thanks

---

