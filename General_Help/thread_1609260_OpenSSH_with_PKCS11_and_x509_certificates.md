---
title: "OpenSSH with PKCS11 and x509 certificates"
date: 2010-10-30
forum: General Help
---

### Post by bitmonkey on 2010-10-30
Hi,

I am trying to set up OpenSSH with x509 certs and I'm getting nowhere. I've been at this on and off for days and doing all the googling I can but I'm still not making progress so any help would be very much appreciated. I believe the latest OpenSSH builds support x509 certificates - I'm running 5.5 on Ubuntu 10.04.

What I want to do is have users on Windows boxes using PuttySC or similar (suggestions welcome) log in without needing to enter a username/password, using an x509 certificate stored on a smartcard / token.

The user identities already exist (x509 certs + private keys) and there is a multi-level CA structure. It's a simple one though:    ROOT CA -> POLICY CA -> ISSUING CA -> USER CERTIFICATE

How do I configure OpenSSH to allow logins from users who have certificates signed by the trusted issuing CA at the end of the chain above. Presumably the server needs the whole CA chain and I've tried cat'ing the .pem files for the CA certificates together and copying the result to a file that I've pointed to with CACertificateFile in sshd_config.

In the authorized_keys I've got:
x509v3-sign-rsa subject= /C=COUNTRY/ST=STATE/O=ORGANIZATION/OU=OU/CN=CN ie. the DN of the ROOT CA certificate - should this instead be the issuing CA?

Generally any pointers would be very helpful, I've found Roumen Petrovs patches and read some of his stuff but I find it a bit difficult to follow and in any case I'm not sure how relevant his implementation is to the mainline openssh 5.4/5.5 x509.

I'd also like to know how I get an x509 certificate into the server for it to use as it's host key, so both the host and users can verify each other using the same CA.

thanks

---

