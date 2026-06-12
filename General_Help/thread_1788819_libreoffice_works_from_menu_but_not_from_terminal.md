---
title: "libreoffice works from menu but not from terminal"
date: 2011-06-23
forum: General Help
---

### Post by ohme on 2011-06-23
from my terminal :
>> libreoffice -writer
gives :
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'

but if I run it from the menu (applications->office->libreoffice writer)
or with sudo it works fine. so something's happening with the permissions, I goes, but I don't quite understand what's wrong. I've tried deleting .libreoffice but this doesn't help

I'm using libreoffice3.3.2 and Ubuntu 11.04.

---

### Post by kleovoulinos on 2011-06-23
I suppose that the only way to get it to work was the way it worked for me:  ```
libreoffice
```

The way I do it is: alt+F2 -> gnome-terminal -> 

username@computername:~$ libreoffice

---

### Post by Gyokuro on 2011-06-23
in terminal: swriter for LibreOffice Writer, scalc for LibreOffice Calc - libreoffice is only a shell script which starts: /usr/lib/libreoffice/program/soffice - you can find the other apps in the same directory.

---

### Post by ohme on 2011-06-23
kleovoulinos : this give me the error message I've discussed.
Gyokuro : swritter does not exist in my system. soffice gives the same error message.

---

### Post by Gyokuro on 2011-06-23
I'm also on Ubuntu 11.04 and have mentioned files; please show us the output of 

which libreoffice

and later use the shown path and show us:

cat libreoffice 

(in my case on Ubuntu 11.04 (up-to-date system) the output of the command and the script file is:   
cat /usr/bin/libreoffice

outbut is in my case:

#!/bin/sh
/usr/lib/libreoffice/program/soffice  "$@"

---

### Post by ohme on 2011-06-23
>  which libreoffice
/usr/bin/libreoffice
> cat /usr/bin/libreoffice
#!/bin/sh
/usr/lib/libreoffice/program/soffice  "$@"


seems similar to yours...

---

### Post by Gyokuro on 2011-06-23
Ok - what happens if you start swriter out of below mentioned directory (cd into it) (as below mentioned directory is libreoffice's app directory). Btw which java version is installed on your system??

---

### Post by ohme on 2011-06-23
this solved the problem! I have no idea why.

I ran it from the /usr/lib/libreoffice/program directory, like you suggested, and it worked, and afterwards it also worked using 

>> libreoffice -writer
from my home directory. 

thanks!

o.s. the java version is 1.6.0_22

---

### Post by ohme on 2011-08-06
It turns out that the problem was not completely solved. the reason I could run libreoffice from the terminal was that some other instance of libre was already open. so this is a kind of work-around : a. lounch libre from the menu. b. lounch other instances from the terminal.

is there a better solution?

---

