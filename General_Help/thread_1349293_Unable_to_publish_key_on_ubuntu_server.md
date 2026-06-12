---
title: "Unable to publish key on ubuntu server"
date: 2009-12-08
forum: General Help
---

### Post by shredder12 on 2009-12-08
Hi everyone, 

I am unable to publish my pgp key on ubuntu key server..
I am using this command..
```
gpg --send-keys --keyserver keyserver.ubuntu.com <key>
```
but after running it I get this error.
```
gpgkeys: HTTP post error 22: The requested URL returned error: 403
gpg: keyserver internal error
gpg: keyserver send failed: keyserver error

```

any suggestions..

---

### Post by shredder12 on 2009-12-09
After trying all the possible methods to publish the key on ubuntu key server I decided to upload it on another public key server [http://keyserver.pgp.com](http://keyserver.pgp.com)
Its more than 12 hrs since the uploaded it but ubuntu keyserver still doesn't seem to recognize it.
Btw. I am unable to open the ubuntu key server website.. [http://keyserver.ubuntu.com:11371](http://keyserver.ubuntu.com:11371)

I am behind a proxy server so could that be an issue?

---

### Post by shredder12 on 2009-12-10
Finally problem solved... I think that the firewall in my network was blocking outgoing connections to port 11371 so I wasn't able to connect to ubuntu keyserver. I tried to open the same url [http://keyserver.ubuntu.com:11371](http://keyserver.ubuntu.com:11371) using a proxy website and it worked even though I was getting some error while submitting key..

So, I uploaded the key on keyserver.noreply.org and ubuntu server got updated in no time. I still don't know what was the problem with pgp keyserver but I was finally able to sign the Ubuntu code of conduct :D

---

