---
title: "Privileges problem."
date: 2009-10-16
forum: General Help
---

### Post by jibidy on 2009-10-16
All I wanted to do is install Flash for safari to run videos and stuff.

when I tried to copy the libflashplayer.so file into the plug-ins directory it said I didn't have the right privileges to do so. I then tried to change the privileges to allow me to write to the system files in the System-administration-users and groups section.

But now for some reason I cant even access that it says

The configuration could not be loaded
You are not allowed access to system configuration.

How can I gain access to the system configuration again?

---

### Post by Mariane on 2009-10-16
Go to where the files are as root and change the owner. 
The command is "chown" and the syntax is explained by:

```

man chown

```

Put yourself as the owner. 

Mariane

---

### Post by jibidy on 2009-10-16
Ok apologies for being a nooby but I don't get it.
What do you mean "Go to where the files are as root"?

And how do I put my self as the owner?

---

### Post by beastrace91 on 2009-10-16
Typically certain file directories are read only to a standard user for a reason - if you just need to copy the one file over (which is what it sounds like - to instal flash correct?)

Press alt+f2 and run ```
gksudo nautilus
``` Then use the file browser it opens to copy over your file.

~Jeff

---

### Post by jibidy on 2009-10-16
I says this

Failed to run nautilus as user root

the underlying authorisation mechanism (sudo) does not allow you to run this program. contact system administrator.

What does this mean? I don't seem to have any authority over this system haha.
Cheers for the help by the way!

---

### Post by beastrace91 on 2009-10-16
Are there any other user accounts on your system? At least one of them should have permission to run things using sudo.

If not you are going need to boot from a LiveCD and edit your sudo user's file to add yourself back to it.

~Jeff

---

### Post by jibidy on 2009-10-16
It only one user. Its just for general use for internet and open office, therefore there is only one account.

Is it straight forward to do. do I need to make another disk? or can I use the disk that I used to install.

---

