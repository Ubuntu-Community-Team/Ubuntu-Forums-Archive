---
title: "FTP client to upload files to AWS S3 bucket"
date: 2012-08-23
forum: General Help
---

### Post by dragonfly41 on 2012-08-23
I have an Amazon AWS S3 bucket and I can use the S3 console to upload files from my localhost ubuntu.

My question .. is there any ubuntu recommended FTP client which can upload files from my localhost to AWS S3 .. something like CloudFTP .. but free?   And can also be scripted to upload.

I use FileZilla for uploading content to EC2 using ssh .. but S3 is different.

I have the AWS API command line tools installed and working if that is relevant.

---

### Post by dragonfly41 on 2012-08-23
Although not a GUI client like FileZilla it seems that **[COLOR=Blue]backup-manager[/COLOR]** (installed via Synaptic Package Manager) might meet my requirements.

In the manual section 2.3.6 - Amazon S3 Uploads

---

### Post by CrusaderAD on 2012-08-23
```
ncftpget
```

Is worth looking into if you're using the command line.

---

### Post by Habitual on 2012-08-23
[http://s3tools.org/s3cmd](http://s3tools.org/s3cmd)...

```
3cmd du -H
2M       s3://c9_nfs_backups/
19M      s3://c9archived/
800M     s3://c9bacula/
93M      s3://c9base804ltsqmi/
7G       s3://c9internal/
1111M    s3://c9prod804ctop061509/
8M       s3://c9prtrip/
508M     s3://c9secucloud02082011/
3G       s3://cirrhusdev02292012/
272M     s3://hiddenslavenode/
```I use the sync option thusly,
```
s3cmd sync /c9backups/c9wiki/ s3://c9internal/c9wiki/
```on a host where the fuse userspace module is inappropriate...

and via /etc/fstab where it is appropriate...
```
s3fs#c9internal        /c9backups         fuse     allow_other,readwrite_timeout=60,connect_timeout=20     0 0
```Tons of options. :)

Subscribed with interest...

---

### Post by dragonfly41 on 2012-08-24
Thanks for those tips .. I'm trying them out ..

I also found this Firefox add on ..

[http://www.s3fox.net/](http://www.s3fox.net/)

---

### Post by Habitual on 2012-09-15
dragonfly41:

Yes, I have and use s3fox occassionally.
NOTE: it does not play well with items stored using the fuse commandline tools. 
The subdirectories I made for my fuse-based backups (ie., s3://c9internal/c9wiki/ ) and populated via those shell scripts, the contents are NOT listed when I use the s3fox v0.6) plugin on any Firefox version since about 4.x.

In short, I do not rely on it to visually show the contents of my backup2s3.sh scripts.

Subscribed with interest...

JJ

---

