---
title: "vsftpd can't see files to download"
date: 2011-04-19
forum: General Help
---

### Post by Shwick2 on 2011-04-19
I recently installed vsftpd and can't see any files I put in the nopriv_user folder.

I want to be able to login anonymously without a password, see files to download and upload files to a pub folder.

After installing and configuring vsftpd I created the ftp_priv user by doing "sudo useradd -d /home/ftp_priv -m ftp_priv".  
Then I added a folder /home/ftp_priv/pub with permissions 777 and a test file.  

vsftpd.conf
```

listen=YES
port_enable=NO
pasv_min_port=55000
pasv_max_port=55100
no_anon_password=YES
max_clients=10
max_per_ip=2
nopriv_user=ftp_priv
anonymous_enable=YES
write_enable=YES
anon_upload_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem

```

I can't see either the folder or file when I connect to my ftp server through my web browser on my local lan windows -> linux server, but I know it's connecting properly because I get a default ftp page and I see this in the vsftpd.log,
```

Tue Apr 19 22:03:32 2011 [pid 2] CONNECT: Client "10.11.12.254"
Tue Apr 19 22:03:32 2011 [pid 1] [ftp] OK LOGIN: Client "10.11.12.254", anon password "<no_password>"

```

I'm using Ubuntu 10.04.2 LTS and vsftpd 2.2.2-3ubuntu6.1.

---

### Post by Shwick2 on 2011-04-20
bleh i looked with wireshark and found "refusing to run with writable anonymous root"

I did chown root:root on /home/ftp_priv and it fixed it o.o

---

