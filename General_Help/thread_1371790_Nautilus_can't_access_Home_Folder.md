---
title: "Nautilus can't access Home Folder"
date: 2010-01-03
forum: General Help
---

### Post by Haruki-kun on 2010-01-03
I can't access the home folder. sudo nautilus in Terminal returned this message:

> 
'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied

You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

Or something to that effect. When Nautilus opened, the screen showed a generic root folder and the only icon was Desktop. Some research led me to install Samba, which reduced the error message to:

> ** (nautilus:4001): WARNING **: Unable to add monitor: Operation not supported

Other info:
I'm the Admin and only User in this computer.
I'm using Ubuntu 9.04 Jaunty Jackalope.
This has never happened before as far as I can tell.

I really need Nautilus to work and I can't figure it out. Can anyone help me?

---

### Post by Haruki-kun on 2010-01-04
Bump.

Please? I really need the help.

---

### Post by jamesisin on 2010-01-04
Do you get an error when you try to login (as your regular user account) about some particular file?  What is it?

---

### Post by mechro on 2010-01-04
Because nautilus is a graphical application you should do **gksudo nautilus**.

Having said that, the behaviour and message you got doing sudo nautilus does not look unusual.

To open your home folder you would usually double-click the Home desktop icon or go to Places > Home Folder. Why are you trying to open it as admin/root?

---

### Post by Haruki-kun on 2010-01-04
> **mechro said:**
> Because nautilus is a graphical application you should do **gksudo nautilus**.

Having said that, the behaviour and message you got doing sudo nautilus does not look unusual.

To open your home folder you would usually double-click the Home desktop icon or go to Places > Home Folder. Why are you trying to open it as admin/root?

I need to change config in mediatomb to stream to PS3.

> **jamesisin said:**
> Do you get an error when you try to login (as your regular user account) about some particular file?  What is it?

No, as a matter off act everything else seems to be working nicely.

---

### Post by mechro on 2010-01-04
OK. do...

**gksudo nautilus**

**Up > home > yourusername** ... Bingo!??

---

### Post by jamesisin on 2010-01-04
Is the mediatomb configuration file located in /home/[username]?  Then open a terminal and navigate to that location and use gksudo gedit mediatomb.config (or whatever the file is named) to edit that file.

---

### Post by buntunoob on 2010-01-07
sudo gedit            to edit the config.xml (if its in /etc/mediatomb/)
 
 
Ive found it in a couple of places
/etc/mediatomb/  or  /home/usr/.mediatomb/
but again that all depends on where you told the start up script that it was

---

### Post by jamesisin on 2010-01-07
You want to use gksudo for gedit and not sudo.  Other than that...

---

