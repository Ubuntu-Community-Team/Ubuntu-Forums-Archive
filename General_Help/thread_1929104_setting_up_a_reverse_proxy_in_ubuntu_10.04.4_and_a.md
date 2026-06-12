---
title: "setting up a reverse proxy in ubuntu 10.04.4 and apache2"
date: 2012-02-21
forum: General Help
---

### Post by johnmerlino on 2012-02-21
Hey all,

I am using Ubuntu 10.04.4 and apache2. I came across two inconsistent tutorials on how to set up a reverse proxy:

[http://blog.janjonas.net/2010-10-09/debian-ubuntu-apache_2-transparent-reverse-proxy-mod_proxy](http://blog.janjonas.net/2010-10-09/debian-ubuntu-apache_2-transparent-reverse-proxy-mod_proxy)

[http://blog.lundscape.com/2009/05/configure-a-reverse-proxy-with-apache/](http://blog.lundscape.com/2009/05/configure-a-reverse-proxy-with-apache/)

[http://ubuntuguide.org/wiki/Apache2_reverse_proxies](http://ubuntuguide.org/wiki/Apache2_reverse_proxies)

Those are three different tutorials with three different approaches. 


First tutorial says to run sudo a2enmod proxy and sudo a2enmod proxy_http and then change virtual host like this:

<VirtualHost *:80>
 
        ServerName your-public-domain.com
 
        <Proxy *>
                Order deny,allow
                Allow from all
        </Proxy>
 
        ProxyPass / [http://your-private-domain.com/](http://your-private-domain.com/)
        ProxyPassReverse / [http://your-private-domain.com/](http://your-private-domain.com/)
 
</VirtualHost>

Second tutorial says run a2enmod proxy_http and change the virtual host to this:

ProxyRequests Off
ProxyPreserveHost On
<Proxy *>
    Order allow,deny
    Allow from all
</Proxy>
ProxyPass /subsonic/ [http://localhost:8180/subsonic/](http://localhost:8180/subsonic/)
ProxyPassReverse /subsonic/ [http://localhost:8180/subsonic/](http://localhost:8180/subsonic/)

Note in the second tutorial they introduce the ProxyRequests and ProxyPreserveHost directives whereas in the first tutorial they dont. First tutorial introduces ServerName directive whereas the second tutorial doesnt. 

What I am personally trying to do is as follows:

when on site abc.com, when I click a link to site auto.efg.com, the browser will load the application on auto.efg.com while mainitaing abc.com on address bar of browser. So if I want to go to auto.efg.com/users/sign_in, then I want to see abc.com/users/sign_in on the address bar.

thanks for any response

---

