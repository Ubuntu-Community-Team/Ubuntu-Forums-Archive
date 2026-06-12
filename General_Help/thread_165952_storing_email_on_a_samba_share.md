---
title: "storing email on a samba share"
date: 2006-04-25
forum: General Help
---

### Post by shannon.cummins on 2006-04-25
I am trying to store my email on my server, and access it using samba from both Windows and Ubuntu (KDE Desktop).  On the Windows side I use thunderbird, and can access the local folders stored on the server with no problem.  When I reboot into Ubuntu, I have tried using Kmail, Enigmail, and the Thunderbird that comes with Ubuntu.  None of which will allow me to type in my samba server address (which I can successfully connect to and browse through Konquerer).  It only allows me to store and retrieve folders and files stored on the local drive.  What am  I missing here, how can I point the mail programs to the local folders stored on the server and not to the ones created on the local drive??

---

### Post by MJN on 2006-04-26
Have you thought about using IMAP enabling you to have a centralised storage of e-mail messages and folders that it universally accessible from anywhere whether that be the server, client on a LAN, or across the Internet? All very simple and workable 'straight out of the box'.

Mathew

---

### Post by NRios on 2007-04-24
> **MJN said:**
> Have you thought about using IMAP enabling you to have a centralised storage of e-mail messages and folders that it universally accessible from anywhere whether that be the server, client on a LAN, or across the Internet? All very simple and workable 'straight out of the box'.

Mathew

What if I'm not the server administrator? From Windows I can access mail located in directory that the server shares using samba with no problems. After a server upgrade, the administrator does not want to use NIS and NFS anymore, so if I want to get to that mail it has to be via samba too.

Nacho.

---

### Post by dcstar on 2007-04-24
> **shannon.cummins said:**
> I am trying to store my email on my server, and access it using samba from both Windows and Ubuntu (KDE Desktop).  On the Windows side I use thunderbird, and can access the local folders stored on the server with no problem.  When I reboot into Ubuntu, I have tried using Kmail, Enigmail, and the Thunderbird that comes with Ubuntu.  None of which will allow me to type in my samba server address (which I can successfully connect to and browse through Konquerer).  It only allows me to store and retrieve folders and files stored on the local drive.  What am  I missing here, how can I point the mail programs to the local folders stored on the server and not to the ones created on the local drive??

Create a link to the folder on the share, and then move the link from the share to where the local directory is expected to be and then shutdown the mail program and rename things to something like this:

```
mv original-mail-directory original-mail-directory.save
mv mail-directory-link original-mail-directory
```

Make sure the permissions of the new link match the old ones, copy all of the files from the .save directory into the new link and then start up your mail program - hopefully it will work! (no guarantee)

---

