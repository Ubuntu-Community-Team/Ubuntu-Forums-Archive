---
title: "apache config"
date: 2009-11-02
forum: General Help
---

### Post by quimkaos on 2009-11-02
Hi all (again :biggrin: )

Does anyone know how i can set apache to list files in a browser on a folder that has no index file (index. html, index.php...) so i can browse files by using FF?

---

### Post by quimkaos on 2009-11-02
had to corectly configure my default file in /etc/apache2/sites-available making it lokk like this:

(...)
DocumentRoot /home/www
(...)
<Directory /home/www/>
        Options **Indexes** FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
</Directory>
(...)

and finally in console:
sudo /etc/init.d/apache2 restart

---

