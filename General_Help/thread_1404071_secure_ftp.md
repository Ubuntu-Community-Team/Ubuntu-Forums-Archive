---
title: "secure ftp"
date: 2010-02-11
forum: General Help
---

### Post by adeelm on 2010-02-11
Hi everyone,

                  I have configured vsftpd on Ubuntu 9.04 and it is working fine. I have configured non-anonymous ftp so that only few of us can acces that ftp. Now I want to secure it using ssl. so I have changed the vsftpd.conf file and entered the following lines in it.

rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=YES
force_local_logins_ssl=YES
force_local_data_ssl=YES

After the restarting the service now when I try to connect to the ftp server it gives me this error.

[SIZE=3][COLOR=Red]530 Non-anonymous sessions must use encryption.[/COLOR][/SIZE]

anyone please tell me the soluion to it.

Thanks

Adeel

---

### Post by adeelm on 2010-02-11
Hi everyone,
                    I did it by using filezilla and it worked just fine as it was before.

Thanks

Adeel

---

