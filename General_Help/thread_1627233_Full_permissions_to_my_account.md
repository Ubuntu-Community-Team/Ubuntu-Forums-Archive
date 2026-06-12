---
title: "Full permissions to my account"
date: 2010-11-21
forum: General Help
---

### Post by KevzJD on 2010-11-21
Hi guys, how do i give full permissions to my account? At the moment i'm logged onto root so i can create files / folders in my LAMP folder (/opt/lampp/htdocs) i've right click on the folder and gone to the permissions tab and give the ownership to my account (Kevin) but it still doesnt let me create files or folders? Any ideas! please help i just want to give my account full permissions to every folder!

---

### Post by matt_symes on 2010-11-21
Hi

Press alt+F2 and type

gksudo nautilus

This will open the file manager (nautilus) with root privileges enbling you to add files where you want. You will have to enter your password. Be careful though with this.

Kind regards

---

### Post by 3rdalbum on 2010-11-21
> **matt_symes said:**
> Hi

Press alt+F2 and type

gksudo nautilus

This will open the file manager (nautilus) with root privileges enbling you to add files where you want. You will have to enter your password. Be careful though with this.

+1; this is the correct way to put files into system locations. DON'T change the permissions of anything outside your home directory, this is a loosening of security policy and if you do it wrong you can really ruin your system. Also, DON'T log in as root - there's a reason why Ubuntu disables the root account by default.

Just open up a root file browser, or run a single command as root, whenever you need to modify something outside your home directory.

---

### Post by KevzJD on 2010-11-21
> **matt_symes said:**
> Hi

Press alt+F2 and type

gksudo nautilus

This will open the file manager (nautilus) with root privileges enbling you to add files where you want. You will have to enter your password. Be careful though with this.

Kind regards

Thanks!, but my problem is that i'm editing PHP files using a php editor under my account and it doesnt let me edit the files due to me not having the correct permissions...

---

### Post by matt_symes on 2010-11-21
Hi

From the command line or Alt + F2

gksudo <name of your editor>

This should start your editor with root privileges.

But my preferred solution is always to edit files in my home directory under my own account and then copy them to the system directories, so i have root access for the bare minimum of time.

Kind regards.

---

