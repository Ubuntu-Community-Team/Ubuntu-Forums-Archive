---
title: "hplip-xxx.run through proxy"
date: 2011-12-02
forum: General Help
---

### Post by Lexus45 on 2011-12-02
Hello all.
I'm not sure if the hplip-3.x.x.run is able to be run when a PC has the access to the Internet only through the proxy server.

During some step of running hplip.run, it tries to connect to the mirror and can not succeed. 
But when I type "export" , Bash shows me that the proxy is set. But hplip.run still can not check for installed components.

```

declare -x ftp_proxy="ftp://proxy.domain.ru:3131/"
declare -x http_proxy="http://proxy.domain.ru:3131/"
declare -x https_proxy="https://proxy.domain.ru:3131/"

```The problem appeared after switching the computer from using NAT to using proxy.

Are there any ideas?

Best regards, Lexus45.

---

### Post by Lexus45 on 2011-12-20
My silly mistake was that I set up the variable "HTTP_PROXY" under normal user, but when we run a command via sudo, it uses root's enviroment, doesn't it ?

So, I've added the bash proxy setting to the root environment.


And I also wrote out the list of packages which are being downloaded during sh hplip-xxx.run (on a PC with NAT available : ) and I installed them before running hplip.run.

If somebody needs this list, here it is:

```
sudo apt-get install python-dev libcups2-dev cups-bsd cups-client cups libusb-dev libtool libcupsimage2-dev libjpeg62-dev openssl libsnmp-dev python-qt4-dbus python-qt4 python-reportlab libdbus-1-dev libsane-dev xsane
```

---

