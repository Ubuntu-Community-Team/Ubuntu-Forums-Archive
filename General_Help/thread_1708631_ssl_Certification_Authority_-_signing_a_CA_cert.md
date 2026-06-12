---
title: "ssl Certification Authority - signing a CA cert"
date: 2011-03-16
forum: General Help
---

### Post by spindler on 2011-03-16
I am having problems creating a SSL certificate. I am using the following instructions.

[https://help.ubuntu.com/10.10/serverguide/C/certificates-and-security.html#generating-a-csr](https://help.ubuntu.com/10.10/serverguide/C/certificates-and-security.html#generating-a-csr)

I set up a Certification Authority on my server so I can sign CA certificates.   See section 6 on the page...titled  " Certification Authority ".

Using these instructions, I created a SSL certificate but I am having problems troubleshooting the website SSL connection.... So I decided to create another certificate to replace it.   I want to create a second certificate to troubleshoot my connection.  I think I have the wrong server.key in place.  I lost the server.key file for my first certificate so I decided to just start over and create a new set of server.key and server.crt.

I created the new server.key and server.csr files and then I used the following command to create the CA authorized crt file.

**sudo openssl ca -in server.csr -config /etc/ssl/openssl.cnf**

After entering the CA pass phrase and answering the questions "Sign the certificate?"  I hit enter and was presented with the following error:

failed to update database
TXT_DB error number 2

So... this is the second certificate I am attempting to sign.  The first one was created rather easily but I cannot create the second.  I took a look at the /etc/ssl/CA/index.tx and it only lists my first certificate.  I took a look at /etc/ssl/CA/serial and it has been updated to 02....which is the next serial number.

1. Any idea what this error is referring to?

---

