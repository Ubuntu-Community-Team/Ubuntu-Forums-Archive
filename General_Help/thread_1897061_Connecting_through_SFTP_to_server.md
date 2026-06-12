---
title: "Connecting through SFTP to server"
date: 2011-12-18
forum: General Help
---

### Post by adamantasaurus on 2011-12-18
Hello,

I'm having trouble connecting to my server through dreamweaver, yesterday it was working fine and I haven't changed anything except I put this code in just a few seconds ago. 

sudo usermod -g www-data [YOUR USERNAME]
sudo chown -R www-data:www-data /var/www
sudo chmod -R 775 /var/www

I'm using Ubuntu Server 10.04 

I'm also using the UFW firewall with ports 80 and 22 open.

Yesterday I also tried installing vsftpd - FTP Server Installation and it gave me an error:
    
```

Err http//us.archive.ubuntu.com/ubuntu/ lucid/main libfile-copy-recursive-perl 0.38-1
Temporary failure resolving 'us.archive.ubuntu.com'
Err http//us.archive.ubuntu.com/ubuntu/ lucid-updates/main update-inetd 4.35ubuntu0.1
Temporary failure resolving 'us.archive.ubuntu.com'
Err http//us.archive.ubuntu.com/ubuntu/ lucid-updates/main vsftpd 2.2.2-3ubuntu6.3
Temporary failure resolving 'us.archive.ubuntu.com'
Err http//us.archive.ubuntu.com/ubuntu/ lucid-security/main vsftpd 2.2.2-3ubuntu6.3
Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://us.archive.ubunt.com/ubuntu/pool/main/libf/libfile-copy-recursive-perl/libfile-copy-recursive-perl_0.38-1_all.deb Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubunt.com/ubuntu/pool/main/u/update0inetd/update-inetd_4.35ubuntu0.1_all.deb Temporary failure resolving 'us.aarchive.ubuntu.com'
Failed to fetch http://security.ubunt.com/ubuntu/pool/main/v/vsftpd/vsftpd_2.2.2-3ubuntu6.3_amd64.deb Temporary failure resolving 'security.ubuntu.com'
E: Unable to fetch some archives, maybr run apt-get update or try with --fix missing?

```

Could you guys help me out?

Thank You in advance

---

### Post by Lars Noodén on 2011-12-18
> **adamantasaurus said:**
> Hello,

sudo usermod -g www-data [YOUR USERNAME]
sudo chown -R www-data:www-data /var/www
sudo chmod -R 775 /var/www



Before moving on to other things, you might want to set the permissions to something safe.  If www-data has write access to the directory, then there is a lot of potential for mischief.  

```

sudo chown -R root.root /var/www

```

If you yourself need write access to it, then you need to have a group that you are a member of and use that.

```

sudo addgroup webmasters

sudo gpasswd --add adamantasaurus  webmasters

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;

```

---

### Post by adamantasaurus on 2011-12-18
> **Lars Noodén said:**
> Before moving on to other things, you might want to set the permissions to something safe.  If www-data has write access to the directory, then there is a lot of potential for mischief.  

```

sudo chown -R root.root /var/www

```

If you yourself need write access to it, then you need to have a group that you are a member of and use that.

```

sudo addgroup webmasters

sudo gpasswd --add adamantasaurus  webmasters

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;

```

Wow thanks,

But unfortunately I don't understand most of what your saying what do yo mean write access. Is there a tutorial you could point me to (or your own advice) that could help me setup the server so I could sftp my website to it (I've read sftp is much more secure than ftp) is there any truth to that?

Thanks

Adamantasaurus

---

### Post by Lars Noodén on 2011-12-18
You can read up on file permissions here:

[list]
[*][https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[*][https://help.ubuntu.com/11.04/ubuntu-help/nautilus-file-properties-permissions.html](https://help.ubuntu.com/11.04/ubuntu-help/nautilus-file-properties-permissions.html)
[/list]

As far as SFTP vs FTP goes, FTP is insecure and cannot be made secure.  It can be wrapped in SSL, but that is a lot of extra effort when SFTP is much simpler to set up.
[list]
[*][http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
[*][http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SFTP_is_not_FTPS](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SFTP_is_not_FTPS)
[/list]

---

### Post by CharlesA on 2011-12-18
> **adamantasaurus said:**
> Wow thanks,

But unfortunately I don't understand most of what your saying what do yo mean write access. Is there a tutorial you could point me to (or your own advice) that could help me setup the server so I could sftp my website to it (I've read sftp is much more secure than ftp) is there any truth to that?

Thanks

Adamantasaurus
Basically www-data should only have read access, since that is all it needs to serve files. If it has write access, it could mess with files.

```
sudo addgroup webmasters
```

This created a group named webmasters

```
sudo gpasswd --add adamantasaurus  webmasters
```

This added your user to the webmasters group

```
sudo chgrp -R webmasters /var/www
```

This changed the group of everything in /var/www to webmasters.

```
sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;
```

These two set the permissions to rw with the sticky bit set so only that group can delete the files.

> **Lars Noodén said:**
> As far as SFTP vs FTP goes, FTP is insecure and cannot be made secure.  It can be wrapped in SSL, but that is a lot of extra effort when SFTP is much simpler to set up.
[list]
[*][http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
[*][http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SFTP_is_not_FTPS](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SFTP_is_not_FTPS)
[/list]

Aye. I use sftp on my home servers and on my web host. So much easier to deal with than regular ftp.

---

### Post by adamantasaurus on 2011-12-18
> **CharlesA said:**
> Basically www-data should only have read access, since that is all it needs to serve files. If it has write access, it could mess with files.

```
sudo addgroup webmasters
```

This created a group named webmasters

```
sudo gpasswd --add adamantasaurus  webmasters
```

This added your user to the webmasters group

```
sudo chgrp -R webmasters /var/www
```

This changed the group of everything in /var/www to webmasters.

```
sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;
```

These two set the permissions to rw with the sticky bit set so only that group can delete the files.



Aye. I use sftp on my home servers and on my web host. So much easier to deal with than regular ftp.


Wow thanks, that makes it much clearer, do I have to put this code in first still?

```


sudo chown -R root.root /var/www

```

Thanks

---

### Post by CharlesA on 2011-12-18
You can run that first, to reset the owner back to root, yeah.

It should be:

```
sudo chown -R root:root /var/www
```

---

### Post by adamantasaurus on 2011-12-18
> **CharlesA said:**
> You can run that first, to reset the owner back to root, yeah.

It should be:

```
sudo chown -R root:root /var/www
```

I put in all the code you told me to put in,

I accidentally put the other code in first though, does that matter?

But now I have another problem I can't connect to my server using dreamweaver it gives me an error saying:

an FTP error occurred can not make connection to host.


What did I do wrong?

---

### Post by CharlesA on 2011-12-18
You'll have to change the group again.

What error is it giving you exactly? Can you connect using sftp from a terminal/WinSCP ?

---

### Post by adamantasaurus on 2011-12-18
> **CharlesA said:**
> You'll have to change the group again.

What error is it giving you exactly? Can you connect using sftp from a terminal/WinSCP ?

the exact error is......

an FTP error occurred can not make connection to host.

I typed the code in with the chown going first (will that change the group again or do I have to do something else)

how do I connect from a terminal/winscp?

I went into the terminal app on my mac and I think I connected to the server it says

Connecting to 192.168.1.72...
The authenticity of host '192.168.1.72 (192.168.1.72)' can't be established.
RSA key fingerprint is 82:40:81:cb:11:9f:e4:5c:ae:19:3d:19:97:23:20:e3.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added '192.168.1.72' (RSA) to the list of known hosts.
adamantasaurus@192.168.1.72's password: 
sftp>

I'm assuming I'm connected

---

### Post by CharlesA on 2011-12-18
Ok, must be something to do with dreamweaver.

Is it trying to use ftp or sftp?

---

### Post by adamantasaurus on 2011-12-18
sftp

---

### Post by CharlesA on 2011-12-18
Huh. 

Try redoing the connection info.

[http://webmaster.iu.edu/tool_guide_info/dreamweaver_pc.shtml](http://webmaster.iu.edu/tool_guide_info/dreamweaver_pc.shtml)

---

### Post by adamantasaurus on 2011-12-18
and the funny thing is I was logged into fine yesterday with dreamweaver

---

### Post by CharlesA on 2011-12-18
> **adamantasaurus said:**
> and the funny thing is I was logged into fine yesterday with dreamweaver
That's the strange thing.

---

### Post by adamantasaurus on 2011-12-18
> **CharlesA said:**
> Huh. 

Try redoing the connection info.

[http://webmaster.iu.edu/tool_guide_info/dreamweaver_pc.shtml](http://webmaster.iu.edu/tool_guide_info/dreamweaver_pc.shtml)

Yea I looked at that tutorial and that won't work for the dreamweaver I have I guess when I go into the advanced tab there is no remote info tab for me to click on. So I just ripped my hair out and downloaded cyberduck. And now that I'm bald I have my website up on my IP address I was wondering if you knew how to get my domain names on there I eventually want to put up three different domain names on my server.

---

### Post by CharlesA on 2011-12-18
You'd have to configure Apache to use VirtualHosts in order to do that.

[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

---

