---
title: "offsite backup"
date: 2010-11-01
forum: General Help
---

### Post by etsmc on 2010-11-01
posted this in the newbie help forum but think this might be a better place for it.
 
**Offsite backup server** 
Hi,
looking for a bit of assistance from those that know. i would like to setup an offsite backup server preferably using my current ubuntu 10.10 server.
i would like something that has a client that can be used on windows PC's and that is managed so i can controll bandwidth and storage space. 
it will only be used for storing important files and not full backups of machines.

i thought about using something like comodo backup for the clients and just setting up and FTP server but just wonderd if people know of a better solution.

Thanks
Adam

similar windows product would be [[COLOR=#444444]ahsay[/COLOR]]("http://www.ahsay.com")

---

### Post by Swiftjay on 2010-11-01
> **etsmc said:**
> posted this in the newbie help forum but think this might be a better place for it.
 
**Offsite backup server** 
Hi,
looking for a bit of assistance from those that know. i would like to setup an offsite backup server preferably using my current ubuntu 10.10 server.
i would like something that has a client that can be used on windows PC's and that is managed so i can controll bandwidth and storage space. 
it will only be used for storing important files and not full backups of machines.

i thought about using something like comodo backup for the clients and just setting up and FTP server but just wonderd if people know of a better solution.

Thanks
Adam

similar windows product would be [[COLOR=#444444]ahsay[/COLOR]]("http://www.ahsay.com")

I would say you could try use cygwin.  That way you can ssh into the windows machine and do a rsync of the files that you want to.  It is a bit of tweaking and configuring to do so.  Sadly I don't know how to do this myself..yet I'm currently trying to figure this out for myself for some clients.

But it would be the safer option as leaving the ftp port open to do such a thing is a major security risk.  Is there no way of you being able to back up the files via external usb hard drive or is the distance too great to do so?

---

### Post by matt_symes on 2010-11-01
Hi

This might be a solution.

[http://www.bacula.org/en/](http://www.bacula.org/en/)

Kind regards

---

### Post by etsmc on 2010-11-02
thanks for the information on those 2 solutions guys but they seem to initiate the backup from the server rather than the client.
I would like to initiate the backup from the client and just have them connect to the server when needed.
 
the windows solution or Ahsay would be the ideal sollution as it has a client that initiates the backup. but its just the cost that we cant be paying out for at the moment.
(plus if its linux based its going to be stable)

---

### Post by etsmc on 2010-11-03
would it be safe to backup to an FTP server if the backup software does the encryption first?? and would it be a good idea to split the backup in to pieces so if there is someone trying to get the information they are less likely to get the whole backup??

---

### Post by matt_symes on 2010-11-03
Hi

If you want to go down the FTP route have you considered SFTP (secure ftp). The are sftp clients for windows and it is automatically encrypted over an ssh connection.
FTP has well known security issues, the least of which is plain text username and password and if your data is sensitive i would not go down that route. There are command line versions under windows, so it could be automated.
SFTP is _much_ more secure esp if you use keys.
I dont really understand how much automation or client user input you want when making these backups.

Kind regards

---

### Post by etsmc on 2010-11-04
well i was looking at using comodo backup to do the backup on the windows machines as it offers backup of files and can encrypt the files and then store on an FTP Site.
 
i have setup pure-ftpd on the ubuntu 10.10 server as it offered quota and bandwidth limiting.
does SFTP allow these features and would comodo be able to connect to it??

---

### Post by etsmc on 2010-11-15
can anyone answer the question on SFTP??

---

### Post by matt_symes on 2010-11-15
Hi

Comodo and sftp? By the looks of it no. 

However here are some testimonials of people on the forum.

[http://forums.comodo.com/empty-t13328.0.html;msg247992](http://forums.comodo.com/empty-t13328.0.html;msg247992)

On poster does lament the lack of sftp support. Read what they have written and see what you think.

Kind regards.

---

### Post by etsmc on 2010-11-16
so what i need to find is a backup software that supports SFTP. but if i do find one (Cobian and comodo have it in the works) 
will the SFTP allow me to do User management and quota limits from what i read its a no but please prove me wrong as i want this to work. :(

---

### Post by etsmc on 2010-12-07
thought i would just like to share that i think i have found a solution for the windows backup client. it is a programe called Duplicati 1.2 and it allows backup to SFTP.

so soon i will start on the whole setup of the server and testing the client software.:D
Wish me luck..

---

### Post by matt_symes on 2010-12-07
Hi

Good luck.  Please post to tell us the softwares efficacy and any issues you encounter.

Kind  regards

---

