---
title: "brother fax 4100 broken install"
date: 2012-05-07
forum: General Help
---

### Post by JeremySchubert on 2012-05-07
Just installed on a new (refurbished) computer to 12.04.    While trying to setup my Brother Fax 4100 printer, I somehow ended up with a package that is 'not fully installed or removed'.  I've tried all sorts of things such as --remove, purge and f but I still keep getting the error message below when I try to run sudo apt-get upgrade (after updating).  Any suggestions welcome, thanks!

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fax4100lpr
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 211698 files and directories currently installed.)
Removing fax4100lpr ...
/var/lib/dpkg/info/fax4100lpr.postrm: 3: /var/lib/dpkg/info/fax4100lpr.postrm: /etc/init.d/lpd: not found
dpkg: error processing fax4100lpr (--remove):
 subprocess installed post-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 fax4100lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by JeremySchubert on 2012-05-07
Well, I don't understand it all, but I found a working solution here:
[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

---

### Post by johnycsf on 2012-12-08
I was having the same problem but I found a way to fix it. 
I still was unable to make my fax4100 work but I fixed the error messages.

Open your terminal. 
#sudo nautilus

go to Computer or File System
go to var/lib/dpkg/info

once there press Ctrl+F and type "fax"
select everything every file with the fax4100 in it and delete it!!!!

close the nautilus window and go back to the terminal.
#sudo apt-get install -f
and select Yes and your error messages will go away!!!

Hope it helps!

---

