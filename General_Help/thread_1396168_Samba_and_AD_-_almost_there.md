---
title: "Samba and AD - almost there"
date: 2010-02-01
forum: General Help
---

### Post by R3d3agl3 on 2010-02-01
[COLOR=black][FONT=Century Gothic]Hello everyone,[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Century Gothic]I have an Ubuntu 8.04.3 with samba 3.0.28a.[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Century Gothic]This server is on an AD network configured on a Windows Server 2003 SBS.[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Century Gothic]Like you might already have guessed, I want configure a Samba share on the Ubuntu server, that can be accessed and managed from the SBS server or it's XP domain posts.[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Century Gothic]To achieve this I've installed and configured Likewise-open following this [/FONT][/COLOR][COLOR=black][FONT=Verdana][[COLOR=blue][FONT=Century Gothic]tutorial[/FONT][/COLOR]]("https://help.ubuntu.com/8.10/serverguide/C/likewise-open.html")[/FONT][/COLOR][COLOR=black][FONT=Century Gothic].[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[LIST]
[*][FONT=Century Gothic]Using [/FONT]*[FONT=Century Gothic]getent group DOMAIN\\user[/FONT]*[FONT=Century Gothic] I'm able to conclude that I've successfully joined the Ubuntu server on the SBS AD.[/FONT][FONT=Verdana][/FONT]
[*][FONT=Century Gothic]I'm also able to login on Ubuntu using DOMAIN\\user authentication[/FONT][FONT=Verdana][/FONT]
[*][FONT=Century Gothic]Finally I'm able to add DOMAIN users to the sudoers list[/FONT][FONT=Verdana][/FONT]
[/LIST][COLOR=black][FONT=Century Gothic]After this, since L[/FONT][/COLOR][COLOR=black][FONT=Century Gothic]ikewise-open[/FONT][/COLOR][COLOR=black][FONT=Century Gothic] and [/FONT][/COLOR][COLOR=black][FONT=Century Gothic]samba[/FONT][/COLOR][COLOR=black][FONT=Century Gothic] packages use separate secrets.tdb files, a symlink was created in /var/lib/samba, using the following commands[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[LIST]
[*]*[FONT=Century Gothic]sudo mv /var/lib/samba/secrets.tdb /var/lib/samba/secrets.tdb.orig[/FONT]*[FONT=Verdana][/FONT]
[*]*[FONT=Century Gothic]sudo ln -s /etc/samba/secrets.tdb /var/lib/samba[/FONT]*[FONT=Verdana][/FONT]
[/LIST][COLOR=black][FONT=Century Gothic]Next, I configured smb.conf like this:[/FONT][/COLOR]
[COLOR=black][FONT=Century Gothic] [/FONT][/COLOR]
*[COLOR=black][FONT=Century Gothic][global][/FONT][/COLOR]*[COLOR=black][FONT=Century Gothic][/FONT][/COLOR]
*[COLOR=black][FONT=Century Gothic] #likewise config[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   security = ADS[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   workgroup = DOMAIN[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   realm = DOMAIN.LOCAL[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   idmap backend = lwopen[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   idmap uid = 50-9999999999[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   idmap gid = 50-9999999999[/FONT][/COLOR]*[COLOR=black][FONT=Century Gothic][/FONT][/COLOR]
*[COLOR=black][FONT=Century Gothic] #config[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   server string = UBUNTUSERVER[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   wins server = SBSSERVER.DOMAIN.SERVER[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   dns proxy = no[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   interfaces = eth0 vmnet8 localhost[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   bind interfaces only = true[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   log file = /var/log/samba/log.%m[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   max log size = 1000[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   syslog = 0[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   encrypt passwords = true[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   passdb backend = tdbsam[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   invalid users = root[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   unix password sync = no[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]   pam password change = no[/FONT][/COLOR]*[COLOR=black][FONT=Century Gothic][/FONT][/COLOR]
[COLOR=black][FONT=Century Gothic] [/FONT][/COLOR]
*[COLOR=black][FONT=Century Gothic][test][/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]      path = /data/teste2[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]      write ok = yes[/FONT][/COLOR]*[I][COLOR=black][FONT=Century Gothic]
[/FONT][/COLOR][/I]*[COLOR=black][FONT=Century Gothic]      inherit permissions = no[/FONT][/COLOR]*[COLOR=black][FONT=Century Gothic][/FONT][/COLOR]
[COLOR=black][FONT=Century Gothic] [/FONT][/COLOR]
[COLOR=black][FONT=Century Gothic]On the Ubuntu server I now have 'root' and 'userA' local users, all the SBS domain users. As a side note, I have a 'DOMAIN\userA'... Same user name and password as the local userA[/FONT][/COLOR]
[COLOR=black][FONT=Century Gothic] [/FONT][/COLOR]
[COLOR=black][FONT=Century Gothic]Now the problems...[/FONT][/COLOR]
[LIST]
[*][FONT=Century Gothic]With all these configurations I'm able to access 'test' share from userA and domain administrator accounts on any XP post.[/FONT]
[*][FONT=Century Gothic]Using the 'security tab' from any Windows machine, I'm able to see the domain.local users.[/FONT]
[*][FONT=Century Gothic]On that share I'm able to create files/folders but when I try to change permissions using the security tab (to add domain users), the changes aren't assumed or, when I try to change ownership I get an "access denied" error.[/FONT]
[/LIST][COLOR=black][FONT=Century Gothic] [/FONT][/COLOR]
[COLOR=black][FONT=Century Gothic]I've tried to change the owner (DOMAIN\Administrator) and group (DOMAIN\All) of the shared folder and subfolders, with a+rwx (full permissions), on the Ubuntu server itself (using chown, chgrp, chmod) but some add of the domain users (from their respective XP post) are prompted for a username and password. The only users that have access are like I said DOMAIN\administrator and DOMAIN\userA.[/FONT][/COLOR]
[COLOR=black][FONT=Century Gothic] [/FONT][/COLOR]
[COLOR=black][FONT=Century Gothic]What am I missing?![/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by R3d3agl3 on 2010-02-23
Is this even possible to achieve?
 
Any replies would be much appreciated...
 
Thanks

---

### Post by jamesisin on 2010-02-23
So you want your Samba share to query against Active Directory for user permissions?

---

### Post by R3d3agl3 on 2010-02-24
Not only that, but I want to be able to manage the Samba share permissions via my Windows domain clients.
I think this is the impossible part

---

### Post by jamesisin on 2010-02-24
I'm not sure that I'm following you.  How would you alter permissions in this scenario?

---

### Post by R3d3agl3 on 2010-03-01
Maybe because what I want to do is impossible...
 
I want to change permissions using the properties->security tab from any xp computer from the same domain.
Like I said, I'm able to list the domain users on the security tab of a samba shared folder, select permissions, but pressing apply they return to the initial settings.
So, is this even possible? :-|
 
Thanks

---

### Post by jamesisin on 2010-03-01
Wow.  I'm not sure.  I would ask the user dmizer:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

I don't know that he'll know, but he knows more than anyone else about Samba.

---

