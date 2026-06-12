---
title: "Apache HTTPs"
date: 2011-06-10
forum: General Help
---

### Post by shubham.joy on 2011-06-10
I installed HTTPs and HTTP apache server.
On accessing [https://localhost](https://localhost) I had this problem

```

HTTPS error ssl_error_rx_record_too_long

```
To solve I changed port number. And now I am getting this error. The server is also not restarting.

```

root@shubham-lappy:/etc/init# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information

```

The log file is:
```

[Thu Jun 09 14:32:55 2011] [notice] Apache/2.2.16 (Ubuntu) configured -- resuming normal operations
[Thu Jun 09 14:32:57 2011] [notice] Graceful restart requested, doing restart
[Thu Jun 09 14:32:57 2011] [notice] Apache/2.2.16 (Ubuntu) configured -- resuming normal operations
[Thu Jun 09 14:55:33 2011] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Jun 09 14:55:36 2011] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Thu Jun 09 17:53:20 2011] [notice] caught SIGTERM, shutting down
[Thu Jun 09 18:40:31 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.5 with Suhosin-Patch configured -- resuming normal operations
[Thu Jun 09 19:06:52 2011] [notice] caught SIGTERM, shutting down
[Thu Jun 09 19:07:37 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.5 with Suhosin-Patch configured -- resuming normal operations
[Thu Jun 09 19:47:30 2011] [notice] caught SIGTERM, shutting down
[Thu Jun 09 20:47:31 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.5 with Suhosin-Patch configured -- resuming normal operations
[Thu Jun 09 21:09:04 2011] [notice] caught SIGTERM, shutting down
[Thu Jun 09 23:23:11 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.5 with Suhosin-Patch configured -- resuming normal operations
[Fri Jun 10 00:29:23 2011] [notice] caught SIGTERM, shutting down
[Fri Jun 10 00:29:25 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.5 with Suhosin-Patch mod_ssl/2.2.16 OpenSSL/0.9.8o configured -- resuming normal operations
[Fri Jun 10 00:30:05 2011] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Jun 10 00:36:39 2011] [notice] caught SIGTERM, shutting down
[Fri Jun 10 00:36:48 2011] [error] Init: Private key not found
[Fri Jun 10 00:36:48 2011] [error] SSL Library Error: 218710120 error:0D094068:asn1 encoding routines:d2i_ASN1_SET:bad tag
[Fri Jun 10 00:36:48 2011] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Fri Jun 10 00:36:48 2011] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
[Fri Jun 10 00:36:48 2011] [error] SSL Library Error: 218734605 error:0D09A00D:asn1 encoding routines:d2i_PrivateKey:ASN1 lib
[Fri Jun 10 00:37:03 2011] [warn] RSA server certificate CommonName (CN) `Shubham' does NOT match server name!?
[Fri Jun 10 00:37:03 2011] [warn] Init: (localhost.localdomain:80) You configured HTTPS(443) on the standard HTTP(80) port!
[Fri Jun 10 00:37:03 2011] [warn] RSA server certificate CommonName (CN) `Shubham' does NOT match server name!?
[Fri Jun 10 00:37:03 2011] [warn] Init: (localhost.localdomain:80) You configured HTTPS(443) on the standard HTTP(80) port!
[Fri Jun 10 00:37:03 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.5 with Suhosin-Patch mod_ssl/2.2.16 OpenSSL/0.9.8o configured -- resuming normal operations
[Fri Jun 10 00:37:16 2011] [error] [client 127.0.0.1] Invalid method in request \x16\x03\x01
[Fri Jun 10 00:42:52 2011] [notice] caught SIGTERM, shutting down
[Fri Jun 10 00:43:21 2011] [warn] RSA server certificate CommonName (CN) `Shubham' does NOT match server name!?
[Fri Jun 10 00:43:21 2011] [warn] Init: (localhost.localdomain:80) You configured HTTPS(443) on the standard HTTP(80) port!
[Fri Jun 10 00:43:21 2011] [warn] RSA server certificate CommonName (CN) `Shubham' does NOT match server name!?
[Fri Jun 10 00:43:21 2011] [warn] Init: (localhost.localdomain:80) You configured HTTPS(443) on the standard HTTP(80) port!
[Fri Jun 10 00:43:21 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.5 with Suhosin-Patch mod_ssl/2.2.16 OpenSSL/0.9.8o configured -- resuming normal operations
[Fri Jun 10 00:43:37 2011] [error] [client 127.0.0.1] Invalid method in request \x16\x03\x01
[Fri Jun 10 00:44:35 2011] [notice] caught SIGTERM, shutting down


```

Please solve this problem.

I am using Ubuntu 10.10 with firefox.

---

### Post by shubham.joy on 2011-06-10
OK I have solved the problem of restarting apache. Undone the port number that I changed earlier.
Now the server is restarting.
But in firefox [http://localhost](http://localhost) and [https://localhost](https://localhost) is not working...
The restart of apache is working.

```

/etc/init.d/apache2 restart
 * Restarting web server apache2                                                 ... waiting Apache/2.2.16 mod_ssl/2.2.16 (Pass Phrase Dialog)
Some of your private key files are encrypted for security reasons.
In order to read them you have to provide the pass phrases.

Server localhost.localdomain:80 (RSA)
Enter pass phrase:

OK: Pass Phrase Dialog successful.
                                                                         [ OK ]
root@shubham-lappy:~# 


```

---

