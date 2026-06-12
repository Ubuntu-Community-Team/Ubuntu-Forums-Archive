---
title: "Citrix on 9.10: client error"
date: 2009-11-11
forum: General Help
---

### Post by paulchinnz on 2009-11-11
Hi need help: after the login screen, when trying to load up an app via Citrix, I get the following message:

Client error:
You have chosen not to trust "COMODO High Assurance Secure Server CA", the issuer of the server's security certificate (SSL error 61).

I'm guessing I have to download the certificates from Comodo (who are comodo?) to some ICAClient folder, but too much of a noob to know where/how. Help please.

---

### Post by paulchinnz on 2009-11-11
Managed to find the certificates and after sudo copying into ./usr/lib/ICAClient/keystore all is well

---

### Post by jt01 on 2010-03-22
> **paulchinnz said:**
> Managed to find the certificates and after sudo copying into ./usr/lib/ICAClient/keystore all is well

I am having the exact same problem and am also having difficulty finding the certificate on the Comodo website.  Do you remember what to download and where to find it on their site?  Thank you - all advice appreciated.

jt01

---

### Post by paulchinnz on 2010-03-23
I can't remember exactly but it was from this:
[https://support.comodo.com/index.php?_m=downloads&_a=view&parentcategoryid=5&pcid=1&nav=0,1](https://support.comodo.com/index.php?_m=downloads&_a=view&parentcategoryid=5&pcid=1&nav=0,1)

---

### Post by jxtreme on 2010-07-21
I am having the same problem. I downloaded this certificate: [https://support.comodo.com/index.php?_m=downloads&_a=viewdownload&downloaditemid=101&nav=0,1,5](https://support.comodo.com/index.php?_m=downloads&_a=viewdownload&downloaditemid=101&nav=0,1,5) and copied it to /usr/lib/ICAClient/keystore and then to /usr/lib/ICAClient/keystore/cacerts, but with no luck. What certificate did you download? Can you look in /usr/lib/ICAClient/keystore?

---

