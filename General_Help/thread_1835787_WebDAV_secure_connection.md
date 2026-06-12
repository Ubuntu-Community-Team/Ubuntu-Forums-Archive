---
title: "WebDAV secure connection"
date: 2011-08-29
forum: General Help
---

### Post by eriktheblu on 2011-08-29
I work for the U.S. Army, and our cloud system has recently added support for WebDAV.

Given that today is the first I've heard of this thing, I'm a bit perplexed.

System is Ubuntu 10.04 64 bit

What I've done so far:

Installed davfs2 package

Mount attempt as follows:
```
eriktheblu@ETBuntu:~$ sudo mount -t davfs https://www.us.army.mil/suite/webdav ~/AKO
Please enter the username to authenticate with server
https://www.us.army.mil/suite/webdav or hit enter for none.
  Username: user.name
Please enter the password to authenticate user user.name with server
https://www.us.army.mil/suite/webdav or hit enter for none.
  Password:  
/sbin/mount.davfs: the server certificate is not trusted
  issuer:      PKI, DoD, U.S. Government, US
  subject:     USA, PKI, DoD, U.S.Government, US
  identity:    www.us.army.mil
  fingerprint: 0a:10:a8:b5:98:57:8c:5e:ae:81:81:3a:a8:1c:a0:12:9c:98:f4:ef
You only should accept this certificate, if you can
verify the fingerprint! The server might be faked
or there might be a man-in-the-middle-attack.
Accept certificate for this session? [y,N] y
/sbin/mount.davfs: Mounting failed.
Could not read status line: Secure connection truncated

```
I downloaded what I believe to be the appropriate certificate to ~/.davfs2/certs and modified /etc/davfs2.conf to show servercert	/home/eriktheblu/.davfs2/certs/www.us.army.mil
No joy.

Commenting that and moving the certificate to ~/.davfs2/cert/private and adding clientcert	/home/eriktheblu/.davfs2/certs/private/www.us.army.mil to the /etc/davfs2.conf resulted in ```
eriktheblu@ETBuntu:~$ sudo mount -t davfs https://www.us.army.mil/suite/webdav ~/AKO
Please enter the username to authenticate with server
https://www.us.army.mil/suite/webdav or hit enter for none.
  Username: user.name
Please enter the password to authenticate user user.name with server
https://www.us.army.mil/suite/webdav or hit enter for none.
  Password:  
/sbin/mount.davfs: can't read client certificate /home/eriktheblu/.davfs2/certs/private/www.us.army.mil

```

This is possibly because as the man page says
> Certificates must be in PKCS#12 format and the only options I have for the certificates seem to be to be available only in other formats (PKCS#7, PEM, in Firefox, Base64-encoded ASCII and DER additionally in Chrome)

I've been able to access the system from my Android phone using an app called WebDAV Navigator Lite with absolutely no problems (it didn't seem to care about the screwy certificates we use)

Any thoughts?
Is this a certificate issue?
Is it possible to employ a smart card for this?

---

### Post by eriktheblu on 2011-08-30
Bump and pondering if my router may have any effect on this. The port forwarding info I've found on WebDAV refers to the server side, so not sure if i need to change anything to just run the client.

I've also tried fusedav, and Nautilus with no luck.

---

