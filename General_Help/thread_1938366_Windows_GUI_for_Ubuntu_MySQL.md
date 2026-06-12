---
title: "Windows GUI for Ubuntu MySQL"
date: 2012-03-09
forum: General Help
---

### Post by SergioQ on 2012-03-09
Am just too new to Unix.   Paid someone to set it all up for me, but time ran out.

I just want a SIMPLE Windows GUI interfacce whwere I can create, manipulate tables, add users, etc.

Somewhere there has to be a site that would walk me through it?

p.s. MySQL Workbench, too much I think.   The one I recall was in Perl or PHP, so clean cut and easy.

It might be the sourcefourge one, but I couldn't find instructions.

Am I that in over my head?

Maybe

Sergio

---

### Post by restorator on 2012-03-09
perhaps you are looking for phpmyadmin? [http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php)

---

### Post by drdos2006 on 2012-03-09
You could install Webmin on your server and access MySql from your desktop browser.


Logon to your server and download from your server with :
sudo wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb)

Install with :
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

Point your desktop browser to https://<server_IP:10000> to edit files, create shares, startup daemons etc..

regards

---

### Post by SergioQ on 2012-03-09
> **restorator said:**
> perhaps you are looking for phpmyadmin? [http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php)

A dollar says this is the one.   Need to go and find screen shots.

Many thanks if it is!

---

### Post by restorator on 2012-03-09
found a link on their site with some screenshots [http://www.phpmyadmin.net/home_page/try.php](http://www.phpmyadmin.net/home_page/try.php)

---

### Post by SergioQ on 2012-03-10
DOne and installled.  This was the one I was looking for.  Many thanks to all.

---

