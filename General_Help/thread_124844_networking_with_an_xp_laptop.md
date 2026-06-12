---
title: "networking with an xp laptop"
date: 2006-02-02
forum: General Help
---

### Post by Choad on 2006-02-02
how would i go about copying files across from this machine to an xp laptop? they are both connected to a wireless router via dhcp. cheers

---

### Post by el3ktro on 2006-02-02
Method 1:
Share any folder on the Win XP machine and connect to this shared folder from the Ubuntu machine.

Method 2:
Install Samba on the Ubuntu machine, share any folder on the Ubuntu machine and connect to this folder from the WinXP machine.

Method 3:
When you have a SSH server running on your machine, install WinSCP on your WinXP machine and you can access your Ubuntu machine like you can access an FTP server.

Tom

---

### Post by Choad on 2006-02-02
ok so method 1, how do i get to the shared folder?

also, the control center is totally messed up and when i click administrator mode, it just goes screwy, so i often cant get access to things :S

---

### Post by el3ktro on 2006-02-02
When you use Ubuntu, click on "Location->Connection to Server". What you have to enter here should be self-explanatory. You can also click on "Locations->Network Server" and Ubuntu should find the workgroup of your WinXP machine.

Tom

---

