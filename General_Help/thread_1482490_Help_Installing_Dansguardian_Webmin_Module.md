---
title: "Help Installing Dansguardian Webmin Module"
date: 2010-05-13
forum: General Help
---

### Post by ashkev on 2010-05-13
Hello,

I have installed squid and Dansguardian on Ubuntu Server 10.04.  I have also installed webmin.  I see that there is a Dansguardian module for Webmin, and I have downloaded it to the server, but I am not sure how to install it.  The file was downloaded from [http://prdownloads.sourceforge.net/dgwebminmodule/dg-0.5.10-pr4.wbm?download](http://prdownloads.sourceforge.net/dgwebminmodule/dg-0.5.10-pr4.wbm?download)
  
I don't know what to do with the .wbm file.

Thanks

Kevin

---

### Post by jaimerosario on 2010-05-19
Download the webmin module and run the following:


/usr/share/webmin/install-module.pl dgwebmin-0.7.0beta1b.wbm # <-- webmin dansguardian module location
sed -i "s|autorestart=0|autorestart=1|" /etc/webmin/dansguardian/config
sed -i "s|file=/sbin|file=/usr/sbin|" /etc/webmin/dansguardian/config
sed -i "s|/rc.d/init.d|/init.d|" /etc/webmin/dansguardian/config
sed -i "s|/rc.d/init.d|/init.d|" /etc/webmin/dansguardian/config

---

