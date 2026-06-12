---
title: "problem with puppet certificates"
date: 2010-05-25
forum: General Help
---

### Post by ffxigotenks on 2010-05-25
I've been trying to get puppet set up on my network, but on the client that I'm testing it with I keep getting 

```
ffxigotenks@Jessica:~$ puppetd --server syraria.local --waitforcert 60 --test
warning: peer certificate won't be verified in this SSL session
info: Caching certificate for ca
warning: peer certificate won't be verified in this SSL session
info: Caching certificate for jessica.example.org
info: Expiring the certificate cache of jessica.example.org
notice: Removing file Puppet::SSL::Certificate jessica.example.org at '/home/ffxigotenks/.puppet/ssl/certs/jessica.example.org.pem'
warning: Retrieved certificate does not match private key
warning: peer certificate won't be verified in this SSL session
info: Caching certificate_request for jessica.example.org
warning: peer certificate won't be verified in this SSL session
info: Caching certificate for jessica.example.org
info: Expiring the certificate cache of jessica.example.org
notice: Removing file Puppet::SSL::Certificate jessica.example.org at '/home/ffxigotenks/.puppet/ssl/certs/jessica.example.org.pem'
warning: Retrieved certificate does not match private key
warning: peer certificate won't be verified in this SSL session
info: Caching certificate for jessica.example.org
info: Expiring the certificate cache of jessica.example.org
notice: Removing file Puppet::SSL::Certificate jessica.example.org at '/home/ffxigotenks/.puppet/ssl/certs/jessica.example.org.pem'
warning: Retrieved certificate does not match private key
warning: peer certificate won't be verified in this SSL session
info: Caching certificate for jessica.example.org
info: Expiring the certificate cache of jessica.example.org
notice: Removing file Puppet::SSL::Certificate jessica.example.org at '/home/ffxigotenks/.puppet/ssl/certs/jessica.example.org.pem'
warning: Retrieved certificate does not match private key
notice: Did not receive certificate
warning: peer certificate won't be verified in this SSL session
info: Caching certificate for jessica.example.org
info: Expiring the certificate cache of jessica.example.org
notice: Removing file Puppet::SSL::Certificate jessica.example.org at '/home/ffxigotenks/.puppet/ssl/certs/jessica.example.org.pem'
warning: Retrieved certificate does not match private key
notice: Did not receive certificate

```

even before I have the server try and sign it, any ideas on why the certificate doesn't match the private key before I ever send it?

---

### Post by surfer on 2010-05-26
sorry, i will not be able to help.

out of curiosity: are you using 10.04 (lucid lynx) and the puppet version that comes with it? i have just started to try it and have run in a lot of problems so far.

---

### Post by surfer on 2010-06-08
oh, i think you should run puppet as root:

```

ffxigotenks@Jessica:~$ **sudo** puppetd --server syraria.local --waitforcert 60 --test
```

---

