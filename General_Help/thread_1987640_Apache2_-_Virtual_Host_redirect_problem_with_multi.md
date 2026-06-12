---
title: "Apache2 - Virtual Host redirect problem with multiple domains"
date: 2012-05-26
forum: General Help
---

### Post by kevtucker on 2012-05-26
Hi, looking for a bit of help with Apache2 on Ubuntu Desktop.

I have 2 names : example1.com and example2.com but having problems with redirecting.

If I type [www.example1.com](www.example1.com) I get my homepage for Example 1
If I type example1.com I get Example 1 homepage again
If I type [www.example2.com](www.example2.com) I get my homepage for Example 2

now the problem here is If I type example2.com it takes me to Example 1 homepage.

I have this in /etc/apache2/apache2.conf at the very bottom :

# Include the virtual host configurations:

Include sites-enabled/

<VirtualHost *:80>
DocumentRoot /Websites/example1
ServerName example1.com
<Directory "/Websites/example1">
allow from all
Options +Indexes
</Directory>
ServerAlias *.example1.com
</VirtualHost>

<VirtualHost *:80>
DocumentRoot /Websites/example2
ServerName example2.com
<Directory "/Websites/example2">
allow from all
Options +Indexes
</Directory>
ServerAlias *.example2.com
</VirtualHost>



Does any one have a solution for me on this. I've tried many things but still not working correctly.

I have my DNS set up on Fasthosts for each domain in A records (www) pointing to my ip address for each domain.

Thank you for any help.

Kevin

---

