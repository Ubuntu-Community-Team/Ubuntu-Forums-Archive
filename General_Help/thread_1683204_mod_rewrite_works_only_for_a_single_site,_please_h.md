---
title: "mod rewrite works only for a single site, please help"
date: 2011-02-07
forum: General Help
---

### Post by Troublesome80 on 2011-02-07
Hi, i use ubuntu 9.04 with lamp and i enabled mod_rewrite module for apache2 so i enabled 3 sites on which i am working. their configuration files in the folder etc/apache2/sites-available are identic even their absolute paths. it'all identic except their names. Below there is the content of one of these configuration files:

FIRST configuration file ->

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/myusername/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/myusername0/www/myfirstsitename/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

SECOND configuration file ->

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/myusername/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/myusername0/www/mysecondsitename/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

Why my .htacces file work only for the first site? another .htacces file in the second site folder does not work. its content it's the same as the other in the first site root folder. it is a simple test rule. it makes non sense, maybe i am wrong and i am neglecting some details, i know, but now i cant see the solution. i need some suggestion.  what can it be the problem? please help me, thank you all anticipately for any suggestion.

---

### Post by SeijiSensei on 2011-02-07
The second virtual host needs a ServerName directive to distinguish it from the first one.

---

### Post by Troublesome80 on 2011-02-08
THANK YOU [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") i guess i have to dome something most complicated before i can distinguish ServerName(s) for each one of my virtualhosts. I have to study how to set the ServerName directive and especially how to get a ServerName for my localhost. Thank you again, now i have not solved the problem but i know the way to solve it. Bye ;)

---

