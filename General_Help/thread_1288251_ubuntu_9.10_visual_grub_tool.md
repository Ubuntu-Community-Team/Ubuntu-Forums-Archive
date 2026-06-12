---
title: "ubuntu 9.10 visual grub tool???"
date: 2009-10-11
forum: General Help
---

### Post by Amgad elsaiegh on 2009-10-11
i,ve just downloaded the beta version of ubuntu 9.10 & i need a visual configuration tool to grub so i can modify the startup options / default Os & time to auto select. in 8.10 , there was "startup manager " , now in 9.10 it do not work correctly :(
Any ideas???:confused:

---

### Post by antony.s on 2009-10-11
Have you tried QGRUBEditor? [http://www.ubuntugeek.com/qgrubeditor-a-visual-grub-configuration-editor.html](http://www.ubuntugeek.com/qgrubeditor-a-visual-grub-configuration-editor.html)

---

### Post by Amgad elsaiegh on 2009-10-12
qgrub is not valid anymore !!!
it gives the following message :
cannot access archive: No such file or directory
any other solutions?

---

### Post by mcduck on 2009-10-12
There isn't one yet, Grub2 is quite new and people haven't really had time to create graphical tools for it.

If I remember right the developer of StartUp-Manager said that he's working on a new version that would support Grub2, but I don't think it's ready yet.

---

### Post by Amgad elsaiegh on 2009-10-12
so we will have to wait :(

---

### Post by CovenStine on 2009-10-12
QGRUBEditor became KGRUBEditor, and so far as I am aware, is available through the default Repositories.  (at least on 9.04... I used it yesterday)

---

### Post by Giblet5 on 2009-10-12
> **CovenStine said:**
> QGRUBEditor became KGRUBEditor, and so far as I am aware, is available through the default Repositories.  (at least on 9.04... I used it yesterday)

Not with Grub 2 (9.10 default), you didn't. ;)

---

### Post by oldfred on 2009-10-12
If you want to change things you can still do it manually. This link has the grub file that has most settings. Scroll down to this
**[SIZE=1]grub (/etc/default/grub)[/SIZE]**


[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by mcduck on 2009-10-12
> **Amgad elsaiegh said:**
> so we will have to wait :(

Yes, but considering that the OS isn't even released yet I'd think it's not a big surprise that it isn't yet well supported by third-party applications..

I mean really, there's still couple of days to kernel freeze & final freeze, it would be way too early to put any considerable effort to developing 3rd party apps before that..

---

### Post by Amgad elsaiegh on 2009-10-12
this manual edit is a little bit complicated & risky :(

---

### Post by mcduck on 2009-10-12
> **Amgad elsaiegh said:**
> this manual edit is a little bit complicated & risky :(

running a beta release is a bit risky. ;)

Besides, the changes you'd need to make to /etc/default/grub are *very* simple. All you need to do is change two numbers in that file ("GRUB_DEFAULT" and "GRUB_TIMEOUT"), save it, and run "sudo update-grub".

---

### Post by Amgad elsaiegh on 2009-10-12
& what about changing the Default Os ?

---

### Post by jeremyswalker on 2009-10-12
> **Amgad elsaiegh said:**
> & what about changing the Default Os ?

That is what GRUB_DEFAULT is for. 0 for the first entry in the menu, 1 for the second, and so on.

---

### Post by Giblet5 on 2009-10-12
I set GRUB_DEFAULT to "saved".

It reboots to whatever I used last time.

---

### Post by Amgad elsaiegh on 2009-10-12
i tried to change the file but while saving the following message appeared

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again

Altough i am the administrator :(
what should i do?!

---

### Post by mcduck on 2009-10-12
> **Amgad elsaiegh said:**
> i tried to change the file but while saving the following message appeared

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again

Altough i am the administrator :(
what should i do?!

You may be administrator, but that doesn't mean that you'd be running with full administrative privileges all the time. That would be stupid, and unsafe, and was one of the main reasons for the security problems in previous Windows versions..:)

Instead, being member of admin group in Ubuntu means that you are able to temporarily gain administrative rights, by using "sudo". You should read this for more detailed information & instructions: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Anyway, in this case the way to open that file for editing with suitable permissions is to open a terminal and then run the following command:
```
gksudo gedit /etc/default/grub
```

---

### Post by Amgad elsaiegh on 2009-10-12
worked flawlessly 
thanks mcduck

---

