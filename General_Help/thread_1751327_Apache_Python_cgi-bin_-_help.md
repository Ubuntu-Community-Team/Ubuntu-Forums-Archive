---
title: "Apache Python cgi-bin - help"
date: 2011-05-06
forum: General Help
---

### Post by Scattered on 2011-05-06
I cannot seem to get my python files to execute under Apache. 

Here is what I have so far:

Apache works. The default page under /var/www renders in a browser.

Python is loaded and works under /etc/bin/python.

I have execute permissions set on /var/www/cgi-bin and my test.py file.

My /etc/apache2/sites-available/default file is this:
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /var/www/cgi-bin/
	<Directory "/var/www/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
                AddHandler cgi-script .py
                AddHandler default-handler .html .htm
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

When I execute this URL: "http://localhost/cgi-bin/test.py" I get this web error: 
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.

The /var/log/apache2/error.log has this error:
[Fri May 06 14:48:08 2011] [error] (2)No such file or directory: exec of '/var/www/cgi-bin/test.py' failed
[Fri May 06 14:48:08 2011] [error] [client 127.0.0.1] Premature end of script headers: test.py

The contents of /var/www/cgi-bin/test.py:
#!/usr/bin/python

print "Content-type:text/html\r\n\r\n"
print '<html>'
print '<head>'
print '<title>Hello Word - First CGI Program</title>'
print '</head>'
print '<body>'
print '<h2>Hello Word! This is my first CGI program</h2>'
print '</body>'
print '</html>'

---

### Post by Scattered on 2011-05-07
Someone suggested that my test.py file might have hidden dos characters (return or line feed characters). I recreated the file using vi which resulted in my file running perfectly.

---

