---
title: "Help with using CA.pl"
date: 2011-03-17
forum: General Help
---

### Post by sgilmour on 2011-03-17
Hi,
I am setting up openssl and freeradius to do peap and tls authentication.
When I enter this command it seems like it runs but nothing happens.
I need it to create these nine certificates.
Thanks
Scott
 
echo "newreq.pem" | /usr/local/openssl/ssl/misc/CA.pl -newca
 
When CA.all executes, it produces nine certificates:
 
root.pem, root.p12, root.der
cert-clt.pem, cert-clt.p12, cert-clt.der
cert-srv.pem, cert-srv.p12, cert-srv.der

---

