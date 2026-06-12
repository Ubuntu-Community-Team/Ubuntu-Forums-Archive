---
title: "&quot;ubuntu 10.10&quot; and &quot;libstdc++-libc6.1-1.so.2&quot;"
date: 2010-11-16
forum: General Help
---

### Post by albejor on 2010-11-16
Hi,

   I have installed Ubuntu 10.10 and I need to run an old Mathematical SW called ADIFOR 3.0. 
  My problem is that this SW is giving problems because has dependencies with the library ""libstdc++-libc6.1-1.so.2". I followed a million of possible ways to fix this problem...but no one works properly.
  What can I do? I have been 3 days trying to fix this problem and I do not know what I can do.

Many thanks

===========================================
Alberto Jorrín Rodríguez
Departamento de Ingenieria de Sistemas y Automatica
Dpt.  of Systems Engineering and Automatic Control
Universidad de Valladolid  / University of Valladolid
Address: Facultad de Ciencias, c/ Real de Burgos s/n
47011 Valladolid, Spain
Tel: +34 647 670 581, Fax: +34 983 423161
e-mail: [email]albejor@autom.uva.es[/email]
============================================

---

### Post by Hippytaff on 2010-11-16
Have you tried installing the missing libraries manualy?
```

sudo apt-get install {library name}

```

---

### Post by albejor on 2010-11-16
Yeah, I tried it...but the  "libstdc++-libc6.1-1.so.2" can not be installed this way...it is a really old file (it came with Red Hat Linux 6.2 for example).
Any other idea?
Many thanks

===========================================
Alberto Jorrín Rodríguez
Departamento de Ingenieria de Sistemas y Automatica
Dpt.  of Systems Engineering and Automatic Control
Universidad de Valladolid  / University of Valladolid
Address: Facultad de Ciencias, c/ Real de Burgos s/n
47011 Valladolid, Spain
Tel: +34 647 670 581, Fax: +34 983 423161
e-mail: [email]albejor@autom.uva.es[/email]
============================================

---

### Post by Hippytaff on 2010-11-16
Try the second post in this thread - [http://ubuntuforums.org/showthread.php?t=237829](http://ubuntuforums.org/showthread.php?t=237829)
The libraries you want are (as you say) Red Hat, whereas ubuntu is debian based. This is why your running into problems.

---

### Post by albejor on 2010-11-16
TThanks for you answer once more!
Unfortunately, when I try the "wget" command tt is said to me that 
/linux/fedora/core/5/x86_64/os/Fedora/RPMS
Is not a directory that currently exists...
The post you sent me is from 2005 so probably the archives there were deleted.
Any other tip?
Many thanks
===========================================
Alberto Jorrín Rodríguez
Departamento de Ingenieria de Sistemas y Automatica
Dpt.  of Systems Engineering and Automatic Control
Universidad de Valladolid  / University of Valladolid
Address: Facultad de Ciencias, c/ Real de Burgos s/n
47011 Valladolid, Spain
Tel: +34 647 670 581, Fax: +34 983 423161
e-mail: [email]albejor@autom.uva.es[/email]
============================================

---

### Post by Hippytaff on 2010-11-16
Thats what I feard - It might be worth searching for a download of the libraries, and there is a way to install rpm stuff on debain systems, but I can't remember how and what the software is called (or you could build it from the binaries if they exist) There is a tutorial in a magazine at home. Will look after work and post it, but in the mean time it might be worth trcking down the libraries :-)
 
Edit -> how about this [http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2006/08/sun-jdk131.html](http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2006/08/sun-jdk131.html)

---

### Post by albejor on 2010-11-16
I really appreciate your help!
I will be looking forward for your new tips...and in the meantime of course I will try to find an answer...
Also I tried to install the Red Hat Linux 6.2 (it is supossed that libstdc++-libc6.1-1.so.2 is here) in my VirtualBox...by this way I can install this Mathematical SW there without having this problem with libstdc++-libc6.1-1.so.2...I tried 3 differents iso´s that I downloaded of Red Hat 6.2 ... but it looks that no one of the works properly and [I]I was not able to install Red Hat...
I will keep trying more things...I must to get the answer! lol
===========================================
Alberto Jorrín Rodríguez
Departamento de Ingenieria de Sistemas y Automatica
Dpt.  of Systems Engineering and Automatic Control
Universidad de Valladolid  / University of Valladolid
Address: Facultad de Ciencias, c/ Real de Burgos s/n
47011 Valladolid, Spain
Tel: +34 647 670 581, Fax: +34 983 423161
e-mail: [email]albejor@autom.uva.es[/email]
============================================




[/I]

---

### Post by Hippytaff on 2010-11-16
Fedora is based on Red Hat. You might have more luck with that!?

---

### Post by albejor on 2010-11-16
Hi,
   Trying the tips I found on the previos link you sent me:
       I tried to install RPM(s) for the GNU stdc++ library.
       I downloaded libstdc++-3.4.6-8.i386.rpm... 
       I executed: rpm -ivh  "package"
       And it doesn´t work cause I only get tons of dependecies of new packages that again I am not able to install using sudo apt-get install
New ideas are welcome!
Many thanks
===========================================
Alberto Jorrín Rodríguez
Departamento de Ingenieria de Sistemas y Automatica
Dpt.  of Systems Engineering and Automatic Control
Universidad de Valladolid  / University of Valladolid
Address: Facultad de Ciencias, c/ Real de Burgos s/n
47011 Valladolid, Spain
Tel: +34 647 670 581, Fax: +34 983 423161
e-mail: [email]albejor@autom.uva.es[/email]
============================================

---

### Post by Hippytaff on 2010-11-16
The package that turn rpm's into deb's and vice versa is called alien
[http://linux.softpedia.com/get/Utilities/Alien-2594.shtml](http://linux.softpedia.com/get/Utilities/Alien-2594.shtml)

And the rpm is here
[http://www.rpmfind.net/linux/rpm2html/search.php?query=libstdc%2B%2B-libc6.1-1.so.2](http://www.rpmfind.net/linux/rpm2html/search.php?query=libstdc%2B%2B-libc6.1-1.so.2)

In theory, once alien is installed, you can type
```

alien -d -k /path/to/rpm

```
It should be converted into a .deb file. You should then be able to instal it :-)

I really hope this works because I don't know what to try after this :-)

---

### Post by albejor on 2010-11-18
Thanks for your answers.
Finally I solved it installing FEDORE CORE 3.0. which is the O.S. that has those dependecies by default.
Cheers.

---

### Post by Hippytaff on 2010-11-18
Glad you sorted it...I thought it would be esiaer to use a red hat derivative :-)
 
Remeber to mark the thread as solved in the thread tools at the top of the page so others with the issue you had can benefit from, what you did :-)

---

### Post by Jouke74 on 2010-11-18
Another option would be to install the Debian library package and it's dependencies of an older distribution e.g. Ubuntu Hardy. I used this way to get a program running which was compiled with Gcc 3.

---

