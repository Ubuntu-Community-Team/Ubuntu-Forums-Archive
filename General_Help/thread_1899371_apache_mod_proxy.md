---
title: "apache mod proxy"
date: 2011-12-23
forum: General Help
---

### Post by adamjseed on 2011-12-23
Hi All,

Im not quite sure this is the best place for this post, I have always had such a good response from these forums  

I am using apache with mod_proxy and headers to reverse proxy sickbeard. 

I have sickbeard is installed on a virtual machine (instanceA) with the web_root set to /sickbeard and port 8081. 

instanceA:8081/sickbeard 

I have Apache2 installed on another virtual machine with a proxy setup as below: 

    SSLEngine On
        SSLProxyEngine on
        SSLCertificateFile    /KEY
        SSLCertificateKeyFile /CERT
        ProxyRequests off

    <Location /tv/>
                ProxyPass [http://instanceA:8081/sickbeard/](http://instanceA:8081/sickbeard/)
                ProxyPassReverse [http://instanceA:8081/sickbeard/](http://instanceA:8081/sickbeard/)
                ProxyHTMLExtended on
                SetOutputFilter proxy-html
                ProxyHTMLURLMap /sickbeard /tv
                ProxyHTMLURLMap /sickbeard/ /tv/

                Order allow,deny
                Allow from all

    </location>

This works great for 90% of Sickbeard's web interface however a couple of javascript links are not being rewritten. For example, if i go into a show and try to select a show from the drop down box 'change show' field, the page redirects to instanceA... Likewise, when changing a shows status, eg. to Wanted, the same happens. Both of these attributes look to be controlled with javascript. 

Has anyone configured Sickbeard to work with Apache2 mod_proxy, or does anyone have  any ideas what else to try? 

Any help would be appreciated. 

Adam.

---

