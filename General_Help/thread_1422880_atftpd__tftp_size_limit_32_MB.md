---
title: "atftpd / tftp size limit 32 MB"
date: 2010-03-05
forum: General Help
---

### Post by altufaltu on 2010-03-05
Hi,

I installed Ubuntu Desktop 9.10 and then apt-get install atftpd tftp. TFTP is working fine but I see that there is a limit of 32 MB on size of file transfer.

I searched through net but it seems atftpd already supports higher file sizes. From the output by tftp, it seems tftp also supports higher file sizes.

However, the file uploaded is limited to 32 MB.

```
$ ls -l -h qt-sdk-win-opensource-2010.02.1.exe
-rwxrwxrwx 1 root root 274M 2010-02-22 18:09 qt-sdk-win-opensource-2010.02.1.exe

$ tftp localhost
tftp> mode binary
tftp> put qt-sdk-win-opensource-2010.02.1.exe
Sent 287174328 bytes in 28.4 seconds
tftp> quit

$ ls -l -h /var/lib/tftpboot/qt-sdk-win-opensource-2010.02.1.exe
-rw-r--r-- 1 nobody nogroup 32M 2010-03-06 14:17 /var/lib/tftpboot/qt-sdk-win-opensource-2010.02.1.exe

$ atftpd -V
atftp-0.7 (server)
```
TFTP client doesn't give any option to see version!

I can't figure out what is the issue.

Please advice.

---

### Post by dcstar on 2010-03-05
> **altufaltu said:**
> Hi,

I installed Ubuntu Desktop 9.10 and then apt-get install atftpd tftp. TFTP is working fine but I see that there is a limit of 32 MB on size of file transfer.
........
However, the file uploaded is limited to 32 MB.

[CODE]$ ls -l -h qt-sdk-win-opensource-2010.02.1.exe
-rwxrwxrwx 1 root root **274M** 2010-02-22 18:09 qt-sdk-win-opensource-2010.02.1.exe

$ tftp localhost
tftp> mode binary
tftp> put qt-sdk-win-opensource-2010.02.1.exe
Sent **287174328** bytes in 28.4 seconds
tftp> quit

$ ls -l -h **/var/lib/tftpboot**/qt-sdk-win-opensource-2010.02.1.exe
-rw-r--r-- 1 nobody nogroup **32M** 2010-03-06 14:17 /var/lib/tftpboot/qt-sdk-win-opensource-2010.02.1.exe

I can't figure out what is the issue.


The file uploaded in **not** limited, the file saved is.

Put the atftpd Base Directory in a folder that is World Readable outside of the Linux system folders with sufficient free space for your uploads.

---

### Post by altufaltu on 2010-03-06
Hi,
 
I did following now:
 
```
USE_INETD=false in /etc/default/atftpd
 
mkdir /tftpboot
chmod -R 777 /tftpboot
chown -R nobody /tftpboot
 
/etc/init.d/atftpd restart
```
 
(All above as root)
 
```
$ rm /tftpboot/qt-sdk-win-opensource-2010.02.1.exe
 
$ echo -e "binary\nput qt-sdk-win-opensource-2010.02.1.exe\n" | tftp localhost
tftp> tftp> Sent 287174328 bytes in 20.6 seconds
tftp> tftp>
 
$ ls -l -h /tftpboot/qt-sdk-win-opensource-2010.02.1.exe
-rw-r--r-- 1 nobody nogroup 32M 2010-03-06 16:28 /tftpboot/qt-sdk-win-opensource-2010.02.1.exe
```
 
There is enough space on disk:
```
$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 71G 13G 55G 19% /
udev 754M 256K 754M 1% /dev
none 754M 128K 754M 1% /dev/shm
none 754M 356K 754M 1% /var/run
none 754M 0 754M 0% /var/lock
none 754M 0 754M 0% /lib/init/rw
none 71G 13G 55G 19% /var/lib/ureadahead/debugfs
```
 
Please advice...

---

### Post by asmoore82 on 2010-03-06
You are aware that TFTP is not FTP, right?
TFTP is meant for PXE booting machines and not general purpose file serving.
see: [http://en.wikipedia.org/wiki/Trivial_File_Transfer_Protocol](http://en.wikipedia.org/wiki/Trivial_File_Transfer_Protocol)

Even still, why not use sftp?
All you have to do is install "openssh-server" and you've got it.

Sorry for changing gears on you, but a 200MB+ *.exe file over TFTP seems a little out of place.

---

### Post by altufaltu on 2010-03-06
Yes. I'm aware that TFTP is not FTP and also not SFTP. I was looking fot a way to anonymous file upload (from win/lin clients) and TFTP server was already installed for other requirements (booting embedded linux).

If TFTP works, that's great. Otherwise I'll look for other means.

N.B. I selected .exe file only because that was readily available big file.

---

### Post by altufaltu on 2010-03-06
I tried with atftp client, but same result.

It is unfortunate that same family of client / server don't work properly :(, but claim to do so...

I'm about to give up.

---

### Post by dcstar on 2010-03-06
> **altufaltu said:**
> I tried with atftp client, but same result.

It is unfortunate that same family of client / server don't work properly :(, but claim to do so...

I'm about to give up.

You are sending to yourself, I'm not sure a primitive protocol like TFTP handles that sort of thing well.

---

### Post by altufaltu on 2010-03-06
OK. Any other alternative?

Can vsftpd allow anonymous ftp upload to /tftpboot folder?

I bet not...

With following in /etc/vsftpd.conf:
```
listen=YES
anonymous_enable=YES
local_enable=NO
write_enable=YES
anon_upload_enable=YES
anon_root=/tftpboot

dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
```

... I get:
500 OOPS: vsftpd: refusing to run with writable anonymous root

... and with anon_root=/ftp, where
mkdir /ftp
ln -s /tftpboot /ftp/tftpboot

... I get:
```
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
lrwxrwxrwx    1 0        0               9 Mar 06 17:53 tftpboot -> /tftpboot
226 Directory send OK.
ftp> cd tftpboot
550 Failed to change directory.
```

I'm flat.

---

### Post by asmoore82 on 2010-03-07
If windoze clients are involved, just share it with samba and allow guest access.

---

### Post by altufaltu on 2010-03-07
I appreciate all suggestions. But I would like to keep things simple.
I'm sorry to deviate attention. Let me focus back to the original topic.

If anyone has a working recipe to have TFTP server & client on Ubuntu to support > 32 MB files, please reply.

Thanks in advance.

---

### Post by dcstar on 2010-03-07
> **altufaltu said:**
> 
.........
If anyone has a working recipe to have TFTP server & client on Ubuntu to support > 32 MB files, please reply.


This works for whole CD images:

[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

---

### Post by altufaltu on 2010-03-08
Thanks, David.

I also found Open TFTP server, which worked out of the box :)
[http://sourceforge.net/projects/tftp-server/](http://sourceforge.net/projects/tftp-server/)

---

