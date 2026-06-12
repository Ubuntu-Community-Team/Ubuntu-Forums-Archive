---
title: "can't configure samba"
date: 2006-05-04
forum: General Help
---

### Post by foxhound_oki on 2006-05-04
hello all, i have installed the package samba so i can have it as my active domain controller.  could someone help me configure it please.

this command:
You may configure the SAMBA server by editing the /etc/samba/smb.conf file to change the default settings or add new settings. More information about each setting is available in the comments of the **_/etc/samba/smb.conf _**file or by viewing the **_/etc/samba/smb.conf _**manual page from the prompt with the following command typed at a terminal prompt: 

gives me the error command:
hash /etc/samba/smb.config: Permission denied.

im logged into the server as the root account.  could some one help me please.  thx

---

### Post by Ramses de Norre on 2006-05-04
Why do you use hash? Doesn't gedit or vi work?

[This]("http://ubuntuforums.org/showthread.php?t=150003&page=2") is a very good explanation about it, look at post #14.

---

### Post by Stormbringer on 2006-05-04
What command did you type to get that error message?

If you are looking for the man-page you would type ...

man smb.conf

If you like to view the contents of /etc/samba/smb.conf you would type ...

less /etc/samba/smb.conf

To edit the file you would type ...

sudo gedit /etc/samba/smb.conf (from within the command line)

OR press ALT+F2 inside of Gnome and enter ...

gksudo gedit /etc/samba/smb.conf


A real ADC (in the terms of Windows 2000 Server / Server 2003) will not be possible ... samba is only able to reassemble a Windows 2000 like PDC (Primary Domain Controller).


So ... what exactly do you need to know about the configuration ... ???

Storm.

---

### Post by foxhound_oki on 2006-05-05
[QUOTE=Stormbringer]What command did you type to get that error message?

If you are looking for the man-page you would type ...

man smb.conf

If you like to view the contents of /etc/samba/smb.conf you would type ...

less /etc/samba/smb.conf

To edit the file you would type ...

sudo gedit /etc/samba/smb.conf (from within the command line)

OR press ALT+F2 inside of Gnome and enter ...

gksudo gedit /etc/samba/smb.conf


A real ADC (in the terms of Windows 2000 Server / Server 2003) will not be possible ... samba is only able to reassemble a Windows 2000 like PDC (Primary Domain Controller).


So ... what exactly do you need to know about the configuration ... ???

Storm.[/QUOTE]

im the school administrator for the technology and computers.  i need a server for people to logon to and have the home folder mapped.  so the server is for user logons and shares.  thats why i need it.  thats all i need is a pdc.  i don't care if it runs like 2000 or 2003.  i just need it.  i can't even edit the files when logged into the root username.  i installed ubuntu server, how can i get gnome when its just a command prompt?   thxs

---

### Post by Stormbringer on 2006-05-05
Ok, on the console you would type (assuming you are logged in as >root<):

# nano -w /etc/samba/smb.conf

This will open the file in nano (Text Editor) for editing.

You may also use "vi" if you are familiar with that one - the handling is rather complex.

If you don't have nano installed:

# apt-get install nano

EDIT: I will look into my backups and post a template smb.conf for you later on...
Meanwhile take a look at HOWTO Forge - there's a nice howto on how to setup a Samba PDC using Breezy:
[http://www.howtoforge.org/samba_setup_ubuntu_5.10](http://www.howtoforge.org/samba_setup_ubuntu_5.10)

---

