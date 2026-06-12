---
title: "Filename characters gets messed up when using unison!"
date: 2006-04-05
forum: General Help
---

### Post by Sethiano on 2006-04-05
Hi all!

I want to sync one local folder on my Ubuntu laptop with one remote folder on my windows computer.

I'm using unison and openssh (the window machine acts as a ssh server).

Now, the problem is that filenames containing native swedish characters (such as åäö) becomes encoded incorrectly.

* When I try to send the the file "åäö.txt" through unison from my ubuntu machine it ends up as "Ã..[and other wierd chars].txt" on my windows machine.   

* When I try to sen the file "åäö.txt" through unison from my windows machine union throws the errormessage: "Glib.convert.Error(1, Invalid byte sequence for UTF-8 string")

I have come to the obvius conclution that there is problems with the character encodings on unbunu (wich uses UTF-8 right ?) and Windows, but how can I solve this problem?

Any help is appreciated!

---

### Post by dcstar on 2006-04-05
[QUOTE=Sethiano]Hi all!

I want to sync one local folder on my Ubuntu laptop with one remote folder on my windows computer.

I'm using unison and openssh (the window machine acts as a ssh server).

Now, the problem is that filenames containing native swedish characters (such as åäö) becomes encoded incorrectly.

* When I try to send the the file "åäö.txt" through unison from my ubuntu machine it ends up as "Ã..[and other wierd chars].txt" on my windows machine.   

* When I try to sen the file "åäö.txt" through unison from my windows machine union throws the errormessage: "Glib.convert.Error(1, Invalid byte sequence for UTF-8 string")

I have come to the obvius conclution that there is problems with the character encodings on unbunu (wich uses UTF-8 right ?) and Windows, but how can I solve this problem?

Any help is appreciated![/QUOTE]

You may need to ensure your system LOCALE matches the Windows machine.

---

### Post by Sethiano on 2006-04-06
Hmm... and how should I do that?

---

### Post by Sethiano on 2006-04-10
I have tried to change the locale in ubuntu (to sv_SE ISO-8859-1), but that did not make any diffrance. So I looked in my Windows locale "Regional and language options" - > Advanced and there is a whole list of non unicode "code page conversion tables". In that list both UTF-8 and the ISO-8859-1 is checked and my default language is set to be swedish. 

Unfortunely, the problem remain ](*,). Is there anybody out there with an idea how to solve this?

---

