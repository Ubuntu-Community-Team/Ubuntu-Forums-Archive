---
title: "Creating subdomain"
date: 2010-12-01
forum: General Help
---

### Post by getmizanur on 2010-12-01
elloo,

i have setup an ubuntu server and i like to add subdomain however i'm not having much luck.

i've created a virtual host

<VirtualHost *:80>
        ServerAdmin [email]webmaster@publishingevents.com[/email]
        ServerName project.xxxxx.com

        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /home/website/public_html/xxxxx.com/trunk

        # Logfiles
        ErrorLog  /home/website/public_html/xxxxx.com/trunk/error.log
        CustomLog /home/website/public_html/xxxxx.com/trunk/access.log combined
</VirtualHost>

project.xxxxx.com is not a valid domain, how do i go about making it a valid domin.

---

### Post by galvatron408 on 2010-12-01
you can either add it to your dns server, tell your isp to add it to their dns server or add it to /etc/hosts.

although, since, if you are asking about it, i'd say contact your isp and have them add it to their dns server. just make sure that your /etc/resolv.conf is pointing to the right dns server.

and... for testing purposes /etc/hosts works great but don't do that to a production server.

---

