---
title: "curlftps error message"
date: 2011-04-27
forum: General Help
---

### Post by cdelellis on 2011-04-27
Hi all
 
I am using a virtual root server from my provider. Everything works fine but one thing. To do backups I want to connect to my providers ftp server. I tried to do so.
 
I installed the packages following the tutorial from 
[FONT=Arial][[COLOR=#0000ff]http://wiki.ubuntuusers.de/curlftpfs[/COLOR]]("http://wiki.ubuntuusers.de/curlftpfs")[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]I added the user to the fuse group and ls -l shows:[/FONT]
[FONT=Arial][EMAIL="root@v37143:/download"]root@v37143:/download[/EMAIL]# ls -l /dev/fuse
crw-rw---- 1 root fuse 10, 229 Apr 27 20:48 /dev/fuse[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]But whenever i start curlftpfs I run into the following error:[/FONT]
[FONT=Arial][EMAIL="root@v37143:/download"]root@v37143:/download[/EMAIL]# curlftpfs 'user:password@backup.1blu.de/' /mnt/ftp_backup/
fuse: failed to open /dev/fuse: Permission denied[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]I would appricate any help on this.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Regards,[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Carsten


[/FONT]

---

