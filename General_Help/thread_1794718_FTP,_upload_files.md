---
title: "FTP, upload files"
date: 2011-07-01
forum: General Help
---

### Post by Beatboxx on 2011-07-01
Hey Guys! I'm working on a media player. Software is Boxee. I made a folder called media in /home/user, where I'm putting all my media. I want to upload files to there from my Windows pc, with ftp. I've installed vsftpd. Config file (without comments) looks like this:

```
listen=YES local_root=/home/bastiaan/media chroot_local_user_enable=YES local_enable=YES write_enable=YES anon_upload_enable=NO use_localtime=YES xferlog_enable=YES connect_from_port_20=YES secure_chroot_dir=/var/run/vsftpd/empty pam_service_name=vsftpd rsa_cert_file=/etc/ssl/private/vsftpd.pem
```When I connect using filezilla (192.168.1.70, my ip, root username+password, no port)
It says connection refused by the server. What am I doing wrong?

---

### Post by Bachstelze on 2011-07-01
If you don't absolutely need FTP (and it doesn't look like it), install openssh-server and use SFTP instead. You can use it with FileZilla too, and it's MUCH less of a hassle to configure.

---

### Post by Beatboxx on 2011-07-01
I've installed openssh:

Try connecting with filezilla:

Response:	fzSftp started
Command:	open "anonymous@192.168.1.70" 22
Command:	Trust new Hostkey: Eenmaal
Command:	Pass: **************
Error:	Authenticatie failed
Error:	Fatal error
Error:	Can't connect with server

What do I need to do? I need to have it working fast, actually....

---

### Post by Beatboxx on 2011-07-01
Anyone?

---

### Post by Dragonbite on 2011-07-01
It looks like it is trying ot log in as "anonymous", do you have a username/password associated with it?

---

### Post by Beatboxx on 2011-07-01
What username/password should I use?

---

### Post by Habitual on 2011-07-01
doh!

---

### Post by Bachstelze on 2011-07-01
> **Beatboxx said:**
> What username/password should I use?

Your login and password on the target system of course. ;)

---

