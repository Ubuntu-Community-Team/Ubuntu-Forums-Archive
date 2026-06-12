---
title: "Perl CGI not working"
date: 2006-06-26
forum: General Help
---

### Post by dgrafix on 2006-06-26
Ive managed to get my apache server to run and php is working.

Trouble is any cgi using perl causes a internal server error.

So far ive installed:

Apache2
PHP5
perl looked like it was already there.

Also, where on earth is the server log located (the one the error talks about) as im dammed if i can find it.

---

### Post by gmcgraw0 on 2006-06-26
Make sure permissions on the script file are correct (I think you need chmod 770 <script name> but I could be wrong... do a google search on "CGI permission apache2"). ALSO (even more importantly) make sure that your web server is set up to do CGIs in the directory where you are placing them.  Apache2 will only run system CGIs under the default configuration and you are required to specify the ExecCGI directive if you want them to run in your home user cgi-bin.

Here is what I put in my apache2.conf to get CGIs running for users:

<Directory /home/*/public_html/cgi-bin>
        AllowOverride FileInfo AuthConfig Limit
        Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
        AllowOverride None
        Order allow,deny
        Allow from all
</Directory>

Hope this helps!

---

### Post by dgrafix on 2006-06-26
interesting,

ive got nothing like that in my apache2.conf, but found the lines in a file called default.000 in a directory called sites-enabled:
ive set this up to my cgi-bin dir:

/var/www is docroot 

	```
ScriptAlias /cgi-bin/ /var/www/cgi-bin/

	<Directory "/var/www/cgi-bin">

		AllowOverride FileInfo AuthConfig Limit
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>


```

permissions on cgis are 755, but still no joy

---

