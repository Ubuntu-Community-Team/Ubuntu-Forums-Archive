---
title: "how do i share print in a network?"
date: 2010-06-04
forum: General Help
---

### Post by origr15 on 2010-06-04
i have a computer with ubuntu 10.04 and one with windows 7 and i want to be able to print from one computer to the other (both have printers) how am i to do this ?

---

### Post by Leppie on 2010-06-04
to share the printer connected to the ubuntu box, go to System>Administration>Printing>Server>Settings and make sure the second option is checked. to view printers shared by other systems check the first option as well.
you still may have to install the printer drivers on your windows box though.

---

### Post by origr15 on 2010-06-04
i know all this but when i try to do it it ask for a password for the windows computer and no matter which password i enter weather it's the windows computer's password or this one's it still says that it's the wrong password.....why?

---

### Post by Leppie on 2010-06-04
i believe that if you want to use the printer connected to the windows box from your linux box, you have to provide the credentials of the windows admin account.

---

### Post by origr15 on 2010-06-04
how?

---

### Post by Morbius1 on 2010-06-04
Do you by any chance have **Windows Live Sign-In Assistant** installed?

Ubuntu is asking you for a password because Windows is asking for a password. Unless you told Windows to password protect the printer it's likely that the Sign-In assistant is getting in the way. It's become the first thing to uninstall to resolve most file / print sharing problems it seems.

[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

[http://ubuntuforums.org/showthread.php?t=1388638](http://ubuntuforums.org/showthread.php?t=1388638)

Just a thought.

---

