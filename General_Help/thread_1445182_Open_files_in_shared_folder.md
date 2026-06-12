---
title: "Open files in shared folder"
date: 2010-04-02
forum: General Help
---

### Post by pycoed on 2010-04-02
I have shared folders on my PC (AMD 64) running 64bit Ubuntu 9.04, which I can connect to via my laptop running Xubuntu 9.10, using Nautilus to browse. So far so good...

However, if I try to open an Openoffice file (.odt, .odg, .ods, etc.) on the laptop from the PC shared folders, all that happens is that a blank  Openwriter/Draw/Calc session opens without the file selected being opened. 
I have tried "Open with" plus "Properties, Open with" set to Openoffice, but to no avail. 
JPG files if I double click them open with Gimp, but if I "Open With " any other app then the same happens as above.
PDF's open OK with Document viewer. So it seems to me to be an issue with file associations to applications, but I can't seem to assocate files with the applications I want!
/etc/gnome/defaults.list looks OK to me ( but what do** I** know?) but I can post this if it helps?

If I copy  files from the shared folder to the laptop, then no problem, but I can't open them direct from the shared folder. Does anyone have any ideas how to fix?

---

### Post by Chesamo on 2010-04-02
Generally, opening shared files accross a network is not recommended.

This is because the network share isn't mounted on a location on your drive... I assume when you go into Nautilus the location looks something like ```
network:///server/share
``` OOo can't use locations like this. Try mounting the network share into something like /media/xubu_share/

Here's something you might find helpful: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by pycoed on 2010-04-02
> **Chesamo said:**
> Generally, opening shared files accross a network is not recommended.

This is because the network share isn't mounted on a location on your drive... I assume when you go into Nautilus the location looks something like ```
network:///server/share
``` OOo can't use locations like this. Try mounting the network share into something like /media/xubu_share/

Here's something you might find helpful: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Yes the location is like that. I'll try mounting as you suggest. Cheers for the info 
I'm intrigued about not opening shared files across a network, though? Isn't that what networks are for? I mean at work, we all open files stored on network shares??:confused:

---

