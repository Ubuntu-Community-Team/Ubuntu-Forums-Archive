---
title: "Squid and ssl"
date: 2010-06-25
forum: General Help
---

### Post by barrowdene on 2010-06-25
I have a squid 2.6 server (reverse proxy) with 3 apache web server on the same box  configured (vhost in the squid conf) , I also have a it pointing to a IIS server on a separate box.

One of the web server on the apache (vhost) server requires https (ssl) access. I have installed a certificate. 

All works well until here and has done for many months .......

Now I need the IIS server to do SSL as well, I have recompiled squid for HTTPS (https_port) installed a self signed certificate on the proxy server. 

But it work allow me to make a ssl connection, I can only do it if I stop the apache2 deamon.

With squid I can forward to many servers on port 80.

If I change the redirect to port 444 for ssl it works, so somehow there is a clash with the SSL port on apache .

How to you do  the same for https ??

Thanks

---

