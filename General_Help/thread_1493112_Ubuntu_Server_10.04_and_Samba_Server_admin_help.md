---
title: "Ubuntu Server 10.04 and Samba Server admin help"
date: 2010-05-25
forum: General Help
---

### Post by jondavidf on 2010-05-25
[FONT=Arial][SIZE=2]Hello all,

I have a LAN of about 70 computers that I would like to share media files between.  I have gotten to the point with Samba that I can view the files without a username/password from client PC's.  I would like to make all the folders read only except for one which will be writable for everyone.  The thing that I am having a hard time with is allowing a couple of administrators (on Windows 7 machines) read/write access for all files/folders.  I am completely new to Ubuntu and Samba so please make explanations thorough.  Here is /etc/samba/smb.conf file:[/SIZE][/FONT][FONT=Arial]
[/FONT]
   [FONT=Arial][SIZE=2][FONT=&quot] [global][/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]   workgroup = WORKGROUP[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]   server string = %h server (Samba, Ubuntu)[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]   wins server = Ubuntu-Server[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]   dns proxy = no[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]   log file = /var/log/samba/log.%m[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]   max log size = 1000[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]   syslog = 0[/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=&quot]    security = user[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]    guest account = nobody[/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=&quot]   encrypt passwords = true[/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=&quot]   passdb backend = tdbsam[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]   obey pam restrictions = yes[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]   unix password sync = yes[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]   passwd program = /usr/bin/passwd %u[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]   passwd chat = *Enter\snew\s*\spassword:* %n\n[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]   map to guest = bad user[/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=&quot][test1][/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]path = /media/2ndhdd/test1[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]readonly = yes[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]browseable = yes[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]guest ok = yes[/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=&quot][test2][/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]path = /media/2ndhdd/test2[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]readonly = yes[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]browseable = yes[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]guest ok = yes[/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=&quot][allusers][/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]path = /media/2ndhdd/allusers[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]writable = no[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]guest ok = yes[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=&quot]browseable = yes[/FONT][/SIZE][/FONT]


[SIZE=2][FONT=Arial]I have messed around with adding admin users = sambaadmin but have had no luck.  I figure this part should be fairly straightforward but I've searched for hours on how to do this.  Thanks for you help.[/FONT][/SIZE]

---

### Post by jondavidf on 2010-05-26
Update:

I now have allowed Samba access to both of my LAN's and have added two administrators to the group via the following lines for each share:

[test1]
....
....
write list = %m Win-PC -u winuser

and then I added winuser as a user on ubuntu and smbpasswd.

The problem I am now having is that squid doesn't seem to be working for the LAN now.  It was only set up on one of them, but no longer works after connecting both LANs via two network cards.

If anyone knows how to help with the Squid/NIC setup please let me know.

Thanks

---

### Post by jondavidf on 2010-06-16
Update:
 
I now have remote admin access to Samba and Squid is working correctly.  The second router added was conflicting the route to the Internet.  I deleted the default route to the second router (gateway) and everything is now working.  You can reference this thread to see what exactly was done:
 
[http://ubuntuforums.org/showthread.php?t=1499910](http://ubuntuforums.org/showthread.php?t=1499910)

---

### Post by jondavidf on 2010-06-16
I am very happy with Samba now.  I only have a couple issues with file sharing now - 

1) The server does not show up in Network Places or Network in Windows machines - have started a new thread for that

2) Two people out of 70 still cannot access files - has to be a Windows problem, so I am starting there

After a power outage today my switch rebooted (server on a UPS) and now I am transferring at 60+ MB/s!

This thread is officially solved.

---

