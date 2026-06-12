---
title: "vsftpd with ftpes refusing datatransfer"
date: 2010-04-21
forum: General Help
---

### Post by azzid on 2010-04-21
I was recently assigned to enchance a ftp-server with SSL/TLS support.

When I started investigating I found out that the server is a virtual (openvz) ubuntu machine with vsftpd.

Enabling ftps was easy enough, I just added the following lines to /etc/vsftpd.conf
```
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=NO
force_local_logins_ssl=NO
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO

```

Then I reloaded vsftpd (/etc/init.d/vsftpd reload). Verified I could still connect with "regular" ftp. Then prepended the ftp url with ftpes:// in filezilla and reconnected.

Upon initial connection I got a notice about my certificate beeing outdated, so I generated a new one:
```
   17  openssl genrsa -out server.key 1024
   18  openssl req -new -x509 -key server.key -out server.pem -days 365
   20  cp /etc/ssl/private/ssl-cert-snakeoil.key /etc/ssl/private/ssl-cert-snakeoil.key-backup
   21  cp /etc/ssl/certs/ssl-cert-snakeoil.pem /etc/ssl/certs/ssl-cert-snakeoil.pem-backup
   22  mv server.key /etc/ssl/private/ssl-cert-snakeoil.key
   23  mv server.pem /etc/ssl/certs/ssl-cert-snakeoil.pem

```

Reloaded my vsftpd again, reconnected with filezilla and that warning was gone! :D

All is not well however, because the encrypted connection always fail to list my files.

Here's the output from filezilla:
```
Status:	Resolving address of ftp.domain.com
Status:	Connecting to 172.16.0.22:21...
Status:	Connection established, waiting for welcome message...
Response:	220 Welcome to FTP server 
Command:	AUTH TLS
Response:	234 Proceed with negotiation.
Status:	Initializing TLS...
Status:	Verifying certificate...
Command:	USER user
Status:	TLS/SSL connection established.
Response:	331 Please specify the password.
Command:	PASS *********
Response:	230 Login successful.
Command:	OPTS UTF8 ON
Response:	200 Always in UTF8 mode.
Command:	PBSZ 0
Response:	200 PBSZ set to 0.
Command:	PROT P
Response:	200 PROT now Private.
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (172,16,0,22,163,245)
Command:	LIST
Response:	150 Here comes the directory listing.
Error:	GnuTLS error -9: A TLS packet with unexpected length was received.
Status:	Server did not properly shut down TLS connection
Error:	Could not read from transfer socket: ECONNABORTED - Connection aborted
Response:	226 Directory send OK.
Error:	Failed to retrieve directory listing
```

When I connect with ftp instead of ftps the file listing works, so what is the difference between listing files with ftps and ftp?
What else might I've missed?

Any help to come around this is appreciated!

---

### Post by azzid on 2010-04-26
I had a notion this could be firewall related (ftp and firewalling is just not a good combination), so today I tested to bypass the firewall, connecting my client to the same subnet as the server. 

The error remain the same though, so there I guess there must really be something wrong with my ftp-config?

No one here got ftpes working?

---

### Post by azzid on 2010-04-26
I found this little [goodie]("http://www.question-defense.com/2010/02/04/vsftpd-error-gnutls-error-9-a-tls-packet-with-unexpected-length-was-received").

After issuing the following:
```
apt-get update; apt-get install vsftpd
```

I got a new version and both ftp and ftpes worked! :D

---

