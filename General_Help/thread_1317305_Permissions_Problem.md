---
title: "Permissions Problem"
date: 2009-11-06
forum: General Help
---

### Post by dave collin on 2009-11-06
I installed and then uninstalled remastersys. I just want to get rid of the remastersys folder that it placed. I can get to it bu up arrowing from my home folder but hitting delete says I don't have permission. Going through terminal with sudo purge command says I cannot and brings up message about seeing system administrator to allow sharing. How do I do this? Has remastersys this been added as a new user, or what? Thanks

---

### Post by RedSingularity on 2009-11-06
Bring up a nautilus window in Admin mode.

Type "sudo nautilus" in a terminal.  Try deleting from there.

---

### Post by dave collin on 2009-11-06
Sorry, should have been more specific - Tried that and get the following:

dave@dave-laptop:~$ sudo nautilus
[sudo] password for dave: 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by RedSingularity on 2009-11-06
What is the full directory of the file you want removed?  Use this command to force delete it.
 
sudo rm -rf /Name/of/file

---

