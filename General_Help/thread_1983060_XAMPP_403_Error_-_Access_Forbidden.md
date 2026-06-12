---
title: "XAMPP 403 Error - Access Forbidden"
date: 2012-05-19
forum: General Help
---

### Post by ojdon on 2012-05-19
Hi there, I am following [this guide]("http://www.codetorment.com/2009/10/20/guide-install-xampp-on-ubuntu/") in order to install XAMPP on the 64-bit Ubuntu 12.04LTS. I have got XAMPP up and running, no problem. Set up all the security and created a symbolic link which links the public_html folder in my home folder to /opt/lampp/htdocs

But when I try and access a site that is saved in the public_html folder (~/public_html/99/index.php) I get the following error in my browser:

> Access forbidden!

You don't have permission to access the requested object. It is either read-protected or not readable by the server.

If you think this is a server error, please contact the webmaster.

Error 403

localhost
Sat 19 May 2012 20:47:20 BST
Apache/2.2.21 (Unix) DAV/2 mod_ssl/2.2.21 OpenSSL/1.0.0c PHP/5.3.8 mod_apreq2-20090110/2.7.1 mod_perl/2.0.5 Perl/v5.10.1

Any help?

---

### Post by gordintoronto on 2012-05-19
That error message looks like it is coming from Apache, not XAMPP. Do you have both of them running? I'm no expert, but that sounds like trouble.

Are you using Ubuntu Desktop or Ubuntu Server?

---

### Post by Lars Noodén on 2012-05-20
XAMPP is a crutch for Windows systems and the wrong way to go about setting up a web server for Linux.  It puts things in weird places and require manual updates.  Set up LAMP instead.  It will be less work and easier and will keep both programs and data in standard locations.

So one solution would be to wipe /opt/lampp and start over by installing the components of your L (Linux), A (Apache/Lighttpd/nginx), M (MySQL/Postgresql), P (Perl/Python/PHP) system. e.g.:

```

sudo apt-get install openssh-server apache2 php5 mysql-server

```

Perl is built in, so that's why you don't need to add it.

With that, you'll find your web pages in a standard location (initially /var/www) and same for your other components.

Most importantly LAMP will use the package manager.  All distros, Ubuntu included, have package managers which take care of downloading and installing. That includes tracking version changes and security updates. You should use the package manager to install the LAMP components rather than attempting to manually maintain them.

---

### Post by ojdon on 2012-05-20
Ah, I'm needing LAMPP for development purposes not for deployment. So I'm just using Ubuntu-Desktop. The "test" pages works as it is in the htdocs folder. But I can't seem to access any folders that are in the ~/public_html which is using a symbolic link to link the two folders together.

---

### Post by Lars Noodén on 2012-05-20
For paths like [font=Courier New]~/public_html[/font] to work you need to activate [per-user directories](https://httpd.apache.org/docs/2.2/howto/public_html.html) module.  Again, though you can add more, Ubuntu gives you one virtual host by default.  The configuration for it is in [font=Courier New]/etc/apache2/sites-available/default[/font].

```

sudo a2enmod userdir
sudo service apache2 restart

```

---

### Post by ojdon on 2012-05-20
But this method isn't compatible with lampp is it? I swear I have used lampp previously on my Netbook using an older version of Ubuntu that just had a symbolic link from one folder in my home folder to another. 

I don't really know how to set up Apache, PHP5 and mysql manually since all I need it for is to test simple HTML5/Javascript projects along with a few other php/mysql related work. So I rather would like to keep using lampp since it is easier to set up. =\ I'm never going to use my machine as a deployment server.

---

### Post by Lars Noodén on 2012-05-21
The method I outlined is standard LAMP.

---

### Post by dakshbhatt21 on 2012-08-31
hey buddy go through this link and if not solve then tell me . . .

[http://daksh21ubuntu.blogspot.com/2012/07/new-xampp-security-concept-problem-in.html](http://daksh21ubuntu.blogspot.com/2012/07/new-xampp-security-concept-problem-in.html)

---

