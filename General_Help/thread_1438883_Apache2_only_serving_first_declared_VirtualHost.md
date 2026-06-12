---
title: "Apache2 only serving first declared VirtualHost"
date: 2010-03-25
forum: General Help
---

### Post by kentuckyShades on 2010-03-25
All,

I have three server names pointing to the same IP address (site1.com, site2.com, and site3.com), however apache2 is redirecting all requests for site2 and site3 to site1 (site1 is my first declared virtual host listed in my sites-available folder). 

These lines are in my httpd.conf file:

Listen 8080
ServerName [http://123.45.67.89:8080](http://123.45.67.89:8080)
DocumentRoot "/media/disk1/mystuff/htdocs"

I have a file /etc/apache2/conf.d/virtual.conf that only contains this line:

NameVirtualHost *:8080

and there are three files in /etc/apache2/sites-available

000-site1.com
001-site2.com
002-site3.com

000-site1.com contains the following:

<VirtualHost *:8080>
        ServerName [www.site1.com](www.site1.com)
        ServerAlias site1.com *.site1.com
        DocumentRoot /media/disk1/mystuff/htdocs/site1.com
        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /media/disk1/mystuff/htdocs/site1.com
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /media/disk1/mystuff/htdocs/site1.com>
		Options +Indexes FollowSymLinks +ExecCGI
		AllowOverride AuthConfig FileInfo
                Order allow,deny
		Allow from all
	</Directory>
        # CGI Directory
        ScriptAlias /cgi-bin/ /media/disk1/mystuff/htdocs/site1.com/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>
        # Logfiles
        ErrorLog  /var/log/apache2/site1.com/error.log
        CustomLog /var/log/apache2/site1.com/access.log combined
</VirtualHost>

site2 and site3 are more or less the same except for these lines...

        ServerName [www.site2.com](www.site2.com)
        ServerAlias site2.com *.site2.com
        DocumentRoot /media/disk1/mystuff/htdocs/site2.com

Why can't apache figure out where to send requests for site2 and site3? What am I missing? Any help would be greatly appreciated!

---

