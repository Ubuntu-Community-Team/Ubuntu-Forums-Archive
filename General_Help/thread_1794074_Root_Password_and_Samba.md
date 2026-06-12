---
title: "Root Password and Samba"
date: 2011-06-30
forum: General Help
---

### Post by alvalente on 2011-06-30
[SIZE=3][FONT=Calibri]I have just installed Ubuntu Server v11.04. It did the same thing that it did to my other server v9.xx when I installed it. It NEVER asks me for a root password just an account name and a password for a user account.  When I try to edit the samba.conf file it will not allow me to do so until I put in the root password so it seems to be a Catch-22. [/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]This version will not even allow me to “shutdown now” unless I have a root password so I am not able to get into the configuration like I am with Server 9.xx.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]What can I do?[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Thanks for any help anyone can provide me.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Sincerely,[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Al Valente[/FONT][/SIZE]

---

### Post by yetiman64 on 2011-06-30
sudo is used to raise a commands privilege to that of root in Ubuntu. The password used for sudo is your user account password. The Rootsudo link in my sig will explain fully the setup in Ubuntu, the root account is locked by default.

In your case the commands would be 
```
gksudo gedit /etc/samba/smb.conf
```if gedit is your text editor, nano could be substituted there (use plain "sudo" with nano - see edit at bottom).
and
```
sudo shutdown now
```and put in your user password (the only user to have sudo use is the original account set up on install, further accounts aren't in the sudoers file automatically)

If you need to do a lot of work as root then the preferred method here is to open a terminal and use ```
sudo -i
``` to get a root shell and put your commands in as normal.
[B]
Edit:[/B] if you have a desktop installed you use gksudo or gksu for graphical applications, that is why I changed the first code with gedit, for nano a terminal or cli application only, plain sudo is fine to use. Once again the Rootsudo link in my sig will explain more fully, the Graphical Sudo section down the page a bit.

---

