---
title: "OpenSSL configuration for Apache 2 on Ubuntu"
date: 2011-08-17
forum: General Help
---

### Post by F. Schnackenpfefferhausen on 2011-08-17
Hello,

in order to share profiles between a Mahara and a Moodle installation I need to get OpenSSL working.

I've got OpenSSL installed on the server and followed [this]("https://help.ubuntu.com/community/OpenSSL") tutorial. However, I still get an error message saying that either OpenSSL or PHPs support for OpenSSL are missing:
> Could not generate a new SSL key. Are you sure that both openssl and the PHP module for openssl are installed on this machine?             
What would be the next steps to actually set up the Apache server and PHP so they can use OpenSSL?
(I've already specified the path to my caconfig.cnf file in Maharas config.php)

---

### Post by F. Schnackenpfefferhausen on 2011-08-23
> **salemeni said:**
> Check in your apache that mod_ssl is installed

Hello,

I've checked that, and it's activated as described [here]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") in section "HTTPS Configuration", the Certificates have been created as described [here]("https://help.ubuntu.com/10.04/serverguide/C/certificates-and-security.html").

**Edit**: Here's the apache error.log, see line 11: [http://pastebin.com/Fa417KEd](http://pastebin.com/Fa417KEd)
**Edit2**: After some further experimenting, here's a bit of the error.log at startup of the server: [http://pastebin.com/HZkVrJCw](http://pastebin.com/HZkVrJCw)

---

### Post by F. Schnackenpfefferhausen on 2011-08-23
I've now added some new information , namely logs to my previous post.

---

### Post by F. Schnackenpfefferhausen on 2011-08-24
Okay I got another update: In a comment in the code that throws the error I can find the following: > // This behaviour has been observed once before, on an ubuntu hardy box. 
            // The php5-openssl package was installed but somehow openssl 
            // wasn't.And this seems to be the case. PHP has the SSL module activated. But I'm also sure SSL exists on the system, since I'm able to do OpenSSL stuff manually.

Where could my configuration error be?

---

