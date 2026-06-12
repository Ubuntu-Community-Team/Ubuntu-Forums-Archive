---
title: "gdm problem cant login"
date: 2010-12-29
forum: General Help
---

### Post by penvy on 2010-12-29
hi there


I have problems with gdm after i login it kicks me back to the login screen. i tried few solutions but it didnt work (only have wifi access, cant use apt-get). I only need to backup few folders before i can reinstall ubuntu but unfortunately i have some command problems with mount. I tried to kill gdm but it didnt help.

How can i set gdm to default? or rather how can i get a provisinal desktop environment?

---

### Post by audiomick on 2010-12-29
> **penvy said:**
> ... I only need to backup few folders before i can reinstall ...
If that is all you need to do, why not just boot into the live CD and save your stuff off from there?

---

### Post by ruben_linux on 2010-12-29
did you try in console mode?

---

### Post by penvy on 2010-12-29
ruben_linux

how can i access from a live cd into my folders? i can see them but i have no permission.

audiomick

i can only use the terminal otherwise i couldnt do anythink cauz its kicks me back to the log in  screen.

---

### Post by Verbeck on 2010-12-29
> **penvy said:**
> 
how can i access from a live cd into my folders? i can see them but i have no permission.


run *gksu nautilus* to open the file browser with root permissions

---

### Post by audiomick on 2010-12-29
> **penvy said:**
> 
how can i access from a live cd into my folders? i can see them but i have no permission.
.


Try starting Nautilus with root privileges.

When you are running from the live CD, open a terminal
System> Accessories >Terminal

and type in

```
gksu nautilus
```You now have an instance of the file manager that has root privileges, and should be able to move your files no matter who they belong to.

---

### Post by penvy on 2010-12-29
at least i gain access. now i need to mark it as trusted.

how can i mark it as trusted?

---

### Post by audiomick on 2010-12-29
You've lost me there. What do you mean "mark as trusted"? :confused:

---

### Post by penvy on 2010-12-29
the folder contents two files 

Access-Your-Private-Data.desktop and a readme


The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.

---

### Post by audiomick on 2010-12-29
That looks like a program is trying to start, or you are trying to start a program.
I thought you were going to try and copy off your data and then re-install.

---

### Post by penvy on 2010-12-29
sorry nevermind. i found my privat files they were hidden. unfortunately they all encrypted.

@Edit

Iam trying to recover it manually.

---

### Post by audiomick on 2010-12-29
Oh dear. Good luck then...

---

### Post by penvy on 2010-12-29
> **audiomick said:**
> Oh dear. Good luck then...

done, peace of cake. gratefully to the encrypted private directory documentation.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory?action=fullsearch&context=180&value=linkto%3A%22EncryptedPrivateDirectory%22](https://help.ubuntu.com/community/EncryptedPrivateDirectory?action=fullsearch&context=180&value=linkto%3A%22EncryptedPrivateDirectory%22)

thank you guys!

btw. 

@ audiomick

ich entschuldige mich nochmals für mein grottenschlechtes englisch.




joyeux noël et bonne année

---

### Post by audiomick on 2010-12-29
> **penvy said:**
> 
@ audiomick

ich entschuldige mich nochmals für mein grottenschlechtes englisch.
joyeux noël et bonne année
Ach was. Ist doch nicht so schlimm...

Glad you got it all sorted.

---

### Post by ruben_linux on 2010-12-29
sorry. but i dont undertand

"Ach was. Ist doch nicht so schlimm..."

my english is very bad.

---

