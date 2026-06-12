---
title: "Permissions Issue"
date: 2006-06-04
forum: General Help
---

### Post by Thund3rstruck on 2006-06-04
Hi all,

 Trying to jump back into Ubuntu but I have some still unresolved issues I can't seem to figure out. 

First,
I understand that only root can run mount and thus I must give out the root password to everyone in order to map their Windows shares in Linux. 

Q:Is there a way around this?

We use several W2K3 windows servers and they do not accept passwords sent by the mount -t smbfs command. If you attempt to use the -o password=myPassword parameter it returns the old "ERRDos:Permission Denied" error. The user must run my script which does not send a password and the windoss server then prompts them for the windows password for each share they need to mount. 

Q: Is there a way I can use the windows equivilent of "SendKeys" to send the password for the user into the shell?

Second,
When we have windows shares mapped in Linux the mount command had to be executed as the root user and thus only root can write to the shares. 

Q: Is there a way to allow Linux user accounts to inherit the permissions of the account that mapped the share (ie: windows user). So for example if you mapped your shares using the -o username=SomeWinAccountName and that account can write to the share, then the linux user should be able to write to the share as well (since we have to mount as root I assume why only root can write as it is now)

The big problem here is that I find myself using the file manager as root and I end up making files that root owns so when I copy them to a windows share none of the windows clients can write to the file and it doesn't even appear to FTP users at all!

---

### Post by taurus on 2006-06-04
Never give out root password unless you are prepared to fix your system in the not so hear future!!!  If you want users to be able to run the mount command, either add those users to sudoer or add them to group adm in /etc/group.  With group adm, they can run any restricted commands with their own password so using sudoer is more reasonable if you only want those users to run the mount command...

---

### Post by Sutekh on 2006-06-04
If a normal user (no sudo privileges) needs to mount a partition, add the **user** flag to the partition line in the /etc/fstab.  That partition then can be mounted without sudo.

---

### Post by Thund3rstruck on 2006-06-04
I considered adding a line into /etc/fstab to mount the shares but since I can't send a password to a Windows 2003 server this way (the server will reject it) it's kind of pointless since the mount will fail. 

So if I understood you correctly, I can add a line in /etc/fstab and even though mounting though fstab will fail the user can mount it manually (or via my script) and not require sudo?

could you show me an example of adding a "user" flag into fstab for a smbfs partition?

Thanks...

---

### Post by Thund3rstruck on 2006-06-05
I'm sure everyone here gets killed with newbies looking for help but I want you all to know that we appreciate all the responses! 

Ultimately I resolved my issue. It turns out that smbfs is not supported anymore as it was replaced by cifs. Cifs allows one to mount Windows 2003 shares without prompting for a password (using a crudentials file). I added the line below in /etc/fstab and the shares are mounted at runtime by the user. 

//192.168.1.1/Files /mnt/server/files cifs uid=linuxuser,credentials=/etc/.cifspw,workgroup=BNETSOFT,user,rw,0 0

For other newbies out there, the crudentials file must be in /etc in order to work. It would not work when located in /home/User

Q: What is linux's environmental variable for the logged on user (ie: %username%) and can I pass it in the fstab file so unique users can map their home (h:\) drives?

---

