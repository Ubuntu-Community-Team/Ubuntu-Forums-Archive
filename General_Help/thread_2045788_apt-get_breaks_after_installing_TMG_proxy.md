---
title: "apt-get breaks after installing TMG proxy"
date: 2012-08-21
forum: General Help
---

### Post by clubbing80s on 2012-08-21
Hi. 

We recently moved from a squid proxy to MS ForFront TMG proxy ( Don't ask lol ). Since then the apt-get updated gives the following  :

Get:1 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libapt-pkg4.12 amd64 0.8.16~exp12ubuntu10.2 [932 kB]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main apt amd64 0.8.16~exp12ubuntu10.2
502 Proxy Error ( The Uniform Resource Locator (URL) does not use a recognized protocol. Either the protocol is not supported or the request was not typed correctly. Confirm that a valid protocol is in use (for example, HTTP for a Web request). ) [IP: 91.189.92.190 80]
Get:2 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libssl1.0.0 amd64 1.0.1-4ubuntu5.3 [1,011 kB]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libapt-inst1.4 amd64 0.8.16~exp12ubuntu10.2
502 Proxy Error ( The Uniform Resource Locator (URL) does not use a recognized protocol. Either the protocol is not supported or the request was not typed correctly. Confirm that a valid protocol is in use (for example, HTTP for a Web request). ) [IP: 91.189.92.190 80] .

If I bypass the proxy completely I get everything works fine. 

I have tested the urls used by apt-get with wget and lynx and they work fine via TMG proxy . So it looks like the issue is isolated to apt-get and TMG , one or both is not following the RFCs or something.

By passing the proxy is not an option for production. 

Anyone seen this before ? 
Any suggestions ?

---

### Post by bodhi.zazen on 2012-08-21
See : [https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

---

### Post by clubbing80s on 2012-08-22
> **bodhi.zazen said:**
> See : [https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

Thanks for the advise . I forgot to mention that the proxy in configured as a transparent proxy. The firewall appliance intercepts the http traffic and redirects it to  the proxy so there is no proxy configuration required on the client side. The TMG replaced a squid proxy that we never had issues with ( we required malware etc scanning ) .



Thanks

G

---

