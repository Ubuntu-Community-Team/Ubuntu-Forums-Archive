---
title: "How to make sure vsftpd is actually using SSL?"
date: 2012-09-11
forum: General Help
---

### Post by tromanow on 2012-09-11
I've successfully, or at least I thought so, configured vsftpd to use SSL. I have:

ssl_enable=YES

I've also generated a key/certificate and added:

rsa_cert_file=/etc/ssl/private/vsftpd.pem


However, to my surprise, I can still connect with a plain old ftp client from linux/windows that surely has never heard about SSL. That tells me I'm not actually using SSL, right?

---

