---
title: "Apache serving default /var/www instead of my virtual name host site"
date: 2011-04-18
forum: General Help
---

### Post by scottmay on 2011-04-18
Hi all,

It will sound like I'm new to Ubuntu because this is a stupidly simple question - I don't know what's going on here.  I'm scripting the re-build of a machine which has been hosting multiple web sites for ages.  I'm testing my upgrade by rolling out a staging machine - staging.webhop.net

When I set up my first virtual host, Apache insists on serving it's default page from /var/www instead of my actual site at /srv/www/staging.webhop.net.

The relevant part of the script is:
```


# install apache2
apt-get -y install apache2
#
# install default website
echo "<VirtualHost *:80>" > /etc/apache2/sites-available/$LONGNAME 
echo "    ServerName $LONGNAME" >> /etc/apache2/sites-available/$LONGNAME
echo "    ServerAlias www.$LONGNAME" >> /etc/apache2/sites-available/$LONGNAME
echo "    DocumentRoot /srv/www/$LONGNAME/public_html/" >> /etc/apache2/sites-available/$LONGNAME
echo "    ErrorLog /srv/www/$LONGNAME/logs/error.log" >> /etc/apache2/sites-available/$LONGNAME
echo "    CustomLog /srv/www/$LONGNAME/logs/access.log combined" >> /etc/apache2/sites-available/$LONGNAME
echo "</VirtualHost>" >> /etc/apache2/sites-available/$LONGNAME
mkdir -p /srv/www/$LONGNAME/public_html
mkdir    /srv/www/$LONGNAME/logs
a2ensite $LONGNAME
a2enmod rewrite
/etc/init.d/apache2 restart
echo "<html><head><title>Welcome</title></head>" > /srv/www/$LONGNAME/public_html/index.html 
echo "<body><p>A place holder page, come back soon</p>" >> /srv/www/$LONGNAME/public_html/index.html 
echo "</body></html>" >> /srv/www/$LONGNAME/public_html/index.html 

```

where $LONGNAME is my website name staging.webhop.net

A file exists after running this script (/etc/apache2/sites-available/staging.webhop.net) :
```

<VirtualHost *:80>
    ServerName staging.webhop.net
    ServerAlias www.staging.webhop.net
    DocumentRoot /srv/www/staging.webhop.net/public_html/
    ErrorLog /srv/www/staging.webhop.net/logs/error.log
    CustomLog /srv/www/staging.webhop.net/logs/access.log combined
</VirtualHost>

```

Logs report that it is definitely serving from /var/www/index.html

What could I have done wrong that should be so easy?

Scott.

---

### Post by SeijiSensei on 2011-04-18
Try putting the configurations in /sites-enabled/ instead.

---

### Post by scottmay on 2011-04-18
Hi there,

When I do the a2ensite command it puts a symlink into the sites-enabled directory, as it should.  It's not that...  Bugger.

---

### Post by scottmay on 2011-04-18
I got it - damn I'm stupid.  I thought I be complete and add my domain name into my hosts file.  Removed the FQDN from my hosts file, leaving a short "machine name" and all is good.  I'm ashamed how much time I wasted on that....

---

