---
title: "disable sudo?"
date: 2006-06-16
forum: General Help
---

### Post by davebradford on 2006-06-16
is there a way to disable sudo? nothing personal! i just prefer using a standard user account and a root account like in fedora!

can anybody help?

thanks..

---

### Post by Ramses de Norre on 2006-06-16
Comment out (or delete) the lines in /etc/sudoers that give permissions to the users you don't want to be able to use sudo.

EDIT: They'll start with the username or %groupname with groupname probably set to admin or adm.

---

### Post by nocturn on 2006-06-16
sudo -s gives you a root shell anyway

you can give passwd from it to enable the root password and clean out the /etc/sudoers file.

Keep in mind that this does break the panel items that invoke gksudo...

---

### Post by davebradford on 2006-06-16
i have commented out everything is that ok?

---

### Post by Ramses de Norre on 2006-06-16
I think so, safest thing to do is edit the file with the visudo command, you can use ```
export EDITOR=vi && sudo visudo
``` for example to use vi (or nano, gedit, whatever). An automatic check for syntax faults is performed on closing the file and output appears in terminal.

---

### Post by davebradford on 2006-06-16
thats ok.. i only use a command line system with no gui.. will this effect anything still?

---

