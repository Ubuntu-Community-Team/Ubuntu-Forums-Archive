---
title: "Home directory deleted?"
date: 2010-03-30
forum: General Help
---

### Post by Jerezano on 2010-03-30
I was trying to get rid of an account so i typed in the terminal  sudo userdel guest  then   sudo rm -r /home// guest   and now  [IMG]http://i40.tinypic.com/2wq9w6e.png[/IMG]  how can i restore my files :'( :'( :'(

---

### Post by zuerston on 2010-03-30
> **Jerezano said:**
> I was trying to get rid of an account so i typed in the terminal  sudo userdel guest  then   sudo rm -r /home// guest   and now  [IMG]http://i40.tinypic.com/2wq9w6e.png[/IMG]  how can i restore my files :'( :'( :'(

Hello
That is your home directory (nava) ,the one with the desktop icon in it,it is empty except for the desktop,dont delete that too!  .
Hit the UP arrow and you will see it

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
[Here's a book on forensics in linux]("http://www.blackhat.com%2Fpresentations%2Fbh-usa-03%2Fbh-us-03-willis-c%2Fbh-us-03-willis.pdf&rct=j&q=Linux+disk+forensic+tools&ei=jWGyS6PEG8P68AbouODyBQ&usg=AFQjCNGWqVmT7CxbCK0CGWPIb1WIRIO3oA") but seriously; good luck.

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
I guess I'm not allowed to make links anymore... [www.blackhat.com%2Fpresentations%2Fbh-usa-03%2Fbh-us-03-willis-c%2Fbh-us-03-willis.pdf&rct=j&q=Linux+disk+forensic+tools&ei=jWGyS6PEG8P68AbouODyBQ&usg=AFQjCNGWqVmT7CxbCK0CGWPIb1WIRIO3oA](www.blackhat.com%2Fpresentations%2Fbh-usa-03%2Fbh-us-03-willis-c%2Fbh-us-03-willis.pdf&rct=j&q=Linux+disk+forensic+tools&ei=jWGyS6PEG8P68AbouODyBQ&usg=AFQjCNGWqVmT7CxbCK0CGWPIb1WIRIO3oA)

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
That one's not working either so... I hope someone else can help you.

---

### Post by 98cwitr on 2010-03-30
make a new user, copy default folders over, chmod a+x the directory underneath your account, run photorec to try and recover lost files if you dont have a viable back...start backing your computer up using 'Simple Backup for Linux'

[http://simplelinuxbkup.sourceforge.net/](http://simplelinuxbkup.sourceforge.net/)

---

