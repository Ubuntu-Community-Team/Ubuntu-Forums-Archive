---
title: "Konsole not configurable"
date: 2006-04-03
forum: General Help
---

### Post by magnusbb on 2006-04-03
Hello,

I am using the very latest KDE 3.5.2 from the Kubuntu mirrors (Breezy). When using Konsole, and trying to run "Configure Konsole" in the "Settings" menu, I am greeted with this: "The specified library konsole could not be found", and it cannot find the file "kcm_konsole.la" in the paths.

Possible reasons for this it says:
 - Error during last upgrade (orphaned module - possible since I've recently upgraded)
 - Old third party modules lying around (not very likely, for me)

can someone please confirm this error?

---

### Post by Barrakketh on 2006-04-03
Works fine for me.

Maybe you could re-install konsole (apt-get --reinstall install konsole)?

---

### Post by magnusbb on 2006-04-03
Thanks for your answer.

Unfortunately it didn't work.

---

### Post by Al3xanR0 on 2006-04-03
Try doing a complete removal (including config files) then install it as if you were for the first time.

---

### Post by magnusbb on 2006-04-03
I tried that too, but then it will take the whole "kdebase" with it, it says.

---

### Post by magnusbb on 2006-04-03
The problem has to be with the packaging. The file Konsole is looking after is "kcm_konsole.la", and it is looking for it in the directory "usr/lib/kde3".

In the earlier packages this file was included, but when I check in the most recent package it is absent.

---

### Post by Al3xanR0 on 2006-04-03
try ```
 find / -name kcm_konsole.la 
``` to see if it exsist on the system if it does you can place a copy of it in the directory or create a symlink to it ```
 ln -s /some/where/kcm_konsole.la /usr/lib/kde3/kcm_konsole.la 
```

---

### Post by njf on 2006-04-03
Confirm the error. Will try in Dapper to see if it presents.

---

### Post by magnusbb on 2006-04-03
The problem is solved. The problem is only with the packaging for Breezy - KDE version 3.5.2. The two files missing are "kcm_konsole.la" and "kcm_konsole.so". Without these, I am unable to configure Konsole.

I then looked in the same package for Dapper, and found that the two files were present in this package. When moving these two files to my "usr/lib/kde3" directory, the problem disappeared.

---

### Post by njf on 2006-04-03
Thanks for the solution.

---

### Post by DeadEyes on 2006-04-04
[QUOTE=magnusbb]The problem is solved. The problem is only with the packaging for Breezy - KDE version 3.5.2. The two files missing are "kcm_konsole.la" and "kcm_konsole.so". Without these, I am unable to configure Konsole.

I then looked in the same package for Dapper, and found that the two files were present in this package. When moving these two files to my "usr/lib/kde3" directory, the problem disappeared.[/QUOTE]

Hi I am having the same problem but I don't understand your solution. What is the name of the package I should be looking for? and can I just download the package and extract the two needed files to the kde3 directory without installing the whole package?

---

### Post by magnusbb on 2006-04-04
Here is the package you probably need:
[http://www.kubuntu.org/packages/kde352/pool-dapper/kdebase/konsole_3.5.2-0ubuntu1_i386.deb](http://www.kubuntu.org/packages/kde352/pool-dapper/kdebase/konsole_3.5.2-0ubuntu1_i386.deb)

Open that package in for example the archiver tool of GNOME, and find the two files I mentioned earlier. Then put the files in that directory I refered to.

---

### Post by DeadEyes on 2006-04-04
thanks magnusbb, I'll give that a try as soon as I get home. Blasted work always getting in the way.

Edit:
thanks again magnusbb that work perfectly

---

### Post by mlord on 2006-04-05
Thanks for debugging this for us!  For the convenience of others, I've placed the two missing files onto my web page for the Dell i9300, with links near the top for a quick retrieval.

[http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/)

Cheers

---

### Post by daiwai on 2006-04-06
Thanks mlord for provinding the files :)

---

### Post by firepol on 2006-04-18
I'm using ubuntu breezy. magnusbb, using your deb was not (for me) a solution, I got this error:

> dpkg -i konsole_3.5.2-0ubuntu1_i386.deb
dpkg: requested operation requires superuser privilege
paul@linux42:~/download$ sudo dpkg -i konsole_3.5.2-0ubuntu1_i386.deb
(Reading database ... 90813 files and directories currently installed.)
Preparing to replace konsole 4:3.5.2-0ubuntu0breezy1 (using konsole_3.5.2-0ubuntu1_i386.deb) ...
Unpacking replacement konsole ...
dpkg: dependency problems prevent configuration of konsole:
 konsole depends on kdelibs4c2a (>= 4:3.5.2); however:
  Package kdelibs4c2a is not installed.
 konsole depends on libgcc1 (>= 1:4.0.2); however:
  Version of libgcc1 on system is 1:4.0.1-4ubuntu9.
 konsole depends on libstdc++6 (>= 4.0.2-4); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
dpkg: error processing konsole (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 konsole

saving mlord files and putting them in the right directories fixed the problem, thanks mlord.

---

### Post by dammit_jim on 2006-04-21
Thanks, mlord. Fixed my konsole settings straight off.

---

### Post by BluenoseJake on 2006-05-06
Thanks for the files.

---

### Post by wh0rd on 2006-05-07
Worked like a charm, thanks for link and the site mlord!

---

### Post by wanger123 on 2006-05-10
Thanks guys!

wanger

---

### Post by dejitarob on 2006-05-10
Most of the Konsole options are still available by right clicking and selecting 'settings'. Thanks for the fix though.

---

