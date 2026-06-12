---
title: "&quot;Connect to server&quot;"
date: 2006-04-23
forum: General Help
---

### Post by datim on 2006-04-23
Hello,

I have never got the "connect to server" option from the places menu when connecting to a Windows Share on a server (in this case win2003) (or other pc) that is in a Windows Domain. How is it meant to work?

Also when first installing Ubuntu 5.10, it gives the option for Windows Domain etc, what actually does that do and how does one change these options after install.

Thanks,
David

---

### Post by sas on 2006-04-23
[QUOTE=datim]Hello,

I have never got the "connect to server" option from the places menu when connecting to a Windows Share on a server (in this case win2003) (or other pc) that is in a Windows Domain. How is it meant to work?[/QUOTE]

You need to know be in the same workgroup/windows domain etc as the windows PC and know all the other neccessary details, then when going to the Places menu in future you should have a "sharename on sharecomputer" shortcut icon which lets you browse the share using Nautilus.

[QUOTE=datim]Also when first installing Ubuntu 5.10, it gives the option for Windows Domain etc, what actually does that do and how does one change these options after install.[/QUOTE]
I don't know much more than it's something to do with Windows networking and you probably want to be in the same domain/workgroup etc as the windows computer. You can edit this information by going to System -> Administration -> Shared Folders. Then pressing Add -> General Windows Share Settings.

---

### Post by datim on 2006-04-28
> 
I don't know much more than it's something to do with Windows networking and you probably want to be in the same domain/workgroup etc as the windows computer. You can edit this information by going to System -> Administration -> Shared Folders. Then pressing Add -> General Windows Share Settings.

Hi,

I've made sure that I'm using the same DOMAIN, I've turned of digital signing in Group Policy of the Win Server 2003 machine. I can connect using the mount command but can not get it to work in the gui in anyway, I just don't get it. Whenever you connect to a share it keeps bringing up the password prompt after correctly entering it.

---

