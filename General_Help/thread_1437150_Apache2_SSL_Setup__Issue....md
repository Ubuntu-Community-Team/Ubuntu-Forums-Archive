---
title: "Apache2 SSL Setup  Issue..."
date: 2010-03-23
forum: General Help
---

### Post by dgohn on 2010-03-23
I followed the tutorial found here [http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html](http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html) but when I try to access [https://www.mydomain.com](https://www.mydomain.com) I get the following:


```

Secure Connection Failed

          

An error occurred during a connection to www.mydomain.com.

SSL received a record that exceeded the maximum permissible length.

(Error code: ssl_error_rx_record_too_long)


```

Not sure what I might have done wrong... I have retraced all of my steps and I don't believe I missed anything.  Any help is appreciated!

---

### Post by dgohn on 2010-03-23
[COLOR=Black]I got an idea and changed [/COLOR][COLOR=Black]the [COLOR=Black]sudo openssl genrsa -des3 -out  server.key 1024 to [/COLOR][COLOR=Black]sudo openssl genrsa -des3 -out  server.key 768 thinking that might help but no cigar. [/COLOR][/COLOR]

---

### Post by dgohn on 2010-03-23
*bump*

---

