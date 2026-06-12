---
title: "Install Citrix in Ubuntu 10.10"
date: 2010-11-13
forum: General Help
---

### Post by mr2v6 on 2010-11-13
Hello everyone,
I would like some help in solving this problem that is bugging me since April this year.

Everytime I install citrix deb client and log in to the citrix address on Firefox, it wouldnt let me in and gives me this full error message in a pop up box.

You have not chosen to trust "GlobalSign Domain Validation CA", the issuer of the server's certificate (SSL error 61)

I googled it and most of the solutions were not as successful as I hope it would be.

Any help would be appreciated.

thanks,
Mr2V6

---

### Post by bradshawd on 2010-11-30
Try this

   1. Download [https://www.verisign.com/support/thawte-roots.zip](https://www.verisign.com/support/thawte-roots.zip)
   2. Extract ThawtePremiumServerCA.cer from the &#8220;Thawte SSLWeb Server Roots&#8221; directory inside the zip.
   3. Copy the cert file to /usr/lib/ICAClient/keystore/cacerts and make sure you rename it to .crt

---

### Post by mr2v6 on 2010-12-09
Hi Bradshawd,
Thanks for the reply.  The copying of cert files work.  However, I took the globalsign rather then the Thawte from the web and that was the one that got rid of the error message.

Best,
Mr2v6

---

### Post by jchoyt on 2011-03-09
This no longer works (at least for me).  Go to [https://www.thawte.com/roots/index.html](https://www.thawte.com/roots/index.html) for the latest information on root certs.  Pull the Thawte Server CA cert (at this point in time, that's Root 3 on their list) and put it in the same directory. So...

```
cd /usr/lib/ICAClient/keystore/cacerts/
sudo wget https://www.thawte.com/roots/thawte_Server_CA.pem

```

---

