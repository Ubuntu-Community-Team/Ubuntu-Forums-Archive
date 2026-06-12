---
title: "Trouble setting up Web Server"
date: 2010-10-23
forum: General Help
---

### Post by Glandoux on 2010-10-23
Hello everyone!
I'm having a really hard time configuring my web server on ubuntu server.
 
Here's my setup.
I created two addresses at dyndns. let's say hello.com and goodbye.com
 
The thing is both address point to the same ip address (My ISP ip)
 
So in my router i did a port forwarding to the static ip address of my web server (say 192.168.0.33 on port 8888).
 
Basically, one website is for me, the other one for my girlfriend.
 
My problem is i can't setup the webserver to differenciate the 2 websites.
If i type hello.com, i will see the content of hello.com (that's good)
If i type goodbye.com, i will see the content of hello.com (not so good..)
 
I did a lot a research, (like the last 2 days) but i'm having a really hard time configuring apache with virtual host. Keep in mind i'm a newbie to all this.. but i didn't find any good info yet on how to do this.
 
Can somebody help me please?
 
Thanks,

---

### Post by efflandt on 2010-10-23
You have to configure name based virtual web hosting, so apache can figure out which local content to serve based the the Host: header in the http request.

Since you are behind a router, you will need to use a wildcard * for VirtualHost IP's. I also set a ServerName that did not resolve publically or was bogus, so my default noname worm trap would work.  The index.html for the nohost path is a single page that leads nowhere.

This is from a very old SuSE version, so paths in Ubuntu may differ, especially for user paths.  Look up the meaning of these settings in the apache documentation.
```
# Override real ServerName from httpd.conf so hostname vhost works
ServerName mainpc.localdomain
UseCanonicalName off
NameVirtualHost *

# Default for unknown access (wormhole and separate log)
<VirtualHost *>
    DocumentRoot /usr/local/httpd/htdocs/nohost
    ServerSignature Off
    ErrorLog /var/log/httpd/nohost_error_log
    LogFormat "%V %h %l %u %t \"%r\" %>s %b" nohost
    CustomLog /var/log/httpd/nohost_access_log nohost
</VirtualHost>

<VirtualHost *>
    DocumentRoot /usr/local/httpd/htdocs/hello
    ServerName hello.com
</VirtualHost>

<VirtualHost *>
    DocumentRoot /usr/local/httpd/htdocs/goodbye
    ServerName goodbye.com
</VirtualHost>
```

---

### Post by SeijiSensei on 2010-10-23
On Ubuntu, you need to put the VirtualHost definitions in /etc/apache2/sites-enabled.  The default file, 000-default, provides the definition for the "It Works!" page that appears if you open [http://localhost/](http://localhost/) on your machine.  Let's modify that file for your purposes:

```

<VirtualHost *:80>
        ### ADD THE NAME OF THE VIRTUAL HOST AS IT APPEARS IN URLs ###
        ServerName hello.example.com
        
        ### MAIL FOR webmaster DELIVERED TO root ###
        ServerAdmin webmaster@localhost
        
        ### CUSTOM DOCUMENT ROOT FOR THIS VIRTUAL HOST ###
        ### See discussion below for option to use /home/username/web ###
        DocumentRoot /var/www/sites/hello
        
        ### REASONABLY RESTRICTIVE DEFAULTS (ESP. NO Indexes) ###
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        ### SOMEWHAT LESS RESTRICTIVE DEFAULTS FOR DocumentRoot ###
        ### MAKE SURE THIS IS IDENTICAL TO DocumentRoot ABOVE  ### 
        <Directory /var/www/sites/hello>
                Options Indexes FollowSymLinks MultiViews

                ### WARNING: "NONE" DENIES ANY CHANGES VIA .htaccess ###
                AllowOverride None

                Order allow,deny
                allow from all
        </Directory>

        ### DROP ScriptAlias IF YOU DON'T USE CGI-BIN SCRIPTS ###
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ### CUSTOM ERROR LOG FILENAME ###
        ErrorLog /var/log/apache2/error-hello.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        ### CUSTOM ACCESS LOG FILENAME ###
        CustomLog /var/log/apache2/access-hello.log combined

</VirtualHost>

```

I've left out the definition of [http://localhost/doc/](http://localhost/doc/) that appears in 000-default since you won't need it.  I've also added modifications so it will accept requests for hello.example.com.  Replace "hello.example.com" in the ServerName directive with the virtual host's name as it would appear in URLs.  I've also set the DirectoryRoot for this virtual host to /var/www/sites/hello (see below for details) and defined custom log files for each site.  Now save this file as /etc/apache2/sites-enabled/001-hello.  Repeat the procedure for the site goodbye.example.com and save the configuration as /etc/apache2/sites-enabled/002-goodbye.  Now restart Apache with "sudo service apache2 restart".  

I specified the directory root as /var/www/sites/hello because I prefer to place each virtual host in a separate subdirectory.  You can also enforce better security on each site since you can control access to the website pages by user and group.  If you follow my approach, you'll need to create /var/www/sites/hello (and goodbye) as root with "sudo mkdir -p /var/www/sites/hello /var/www/sites/goodbye".  Place the pages for the hello and goodbye sites in their respective directories under /var/www/sites.  

An alternative is place these directories under the user's $HOME, say /home/username/web, but that requires changes to permissions.  By default homes have 700 permissions meaning only the user can read or write in $HOME.  Since web pages have to be world-readable, you need to enable visitors to see that directory.  You need to grant at least 0711 permissions to /home/username for each user with a web site.  This means it's possible for me to list the directories under your account even if I cannot read the files they contain.  In this approach, you'd use 0755 permissions for any /home/username/web directories and subdirectories.  Pages should have 644 permissions.  This method lets you log into Ubuntu and manage your own site.  Placing the content under /var/www limits changes to the root user.

Now Apache should answer requests from any HTTP client on any interface and display different pages for hello.example.com and goodbye.example.com.

---

### Post by efflandt on 2010-10-23
I just installed apache2 in Maverick as the result of checking something else out.  Apparently the default configuration must already have NameVirtualHost enabled because the following added as new file **/etc/apache2/sites-enabled/myvhosts.conf** works.  Note that my PC name was already in /etc/hosts and I added 127.0.1.2 for deffland:

```
UseCanonicalName off

<VirtualHost *:80>
    DocumentRoot /home/efflandt/public_html
    ServerName efflandt-desktop
</VirtualHost>
<VirtualHost *:80>
    DocumentRoot /home/deffland/public_html
    ServerName deffland
</VirtualHost>
```In a URL, **localhost** serves from /var/www/, **efflandt-desktop** serves /home/efflandt/public_html/, and **deffland** serves /home/deffland/public_html/

I have not tried it with pubic DNS, but it works as well from another PC in my LAN when in /etc/hosts of client PC I assign the LAN IP of the server as efflandt-desktop deffland maverick.  In that case maverick points to the 000-default.conf main path /var/www because the name does not match any other vhost.  Note that you would want to use your public names for ServerName in vhost sections, but you can have additional (local or public) names for each vhost using ServerAlias.  And you may want to add other directives.

---

### Post by Glandoux on 2010-10-23
It works now!
thanks a bunch!

---

### Post by SeijiSensei on 2010-10-24
> **efflandt said:**
> Apparently the default configuration must already have NameVirtualHost enabled

Yes, in /etc/apache2/ports.conf.

---

### Post by johnmay on 2010-11-26
I have set up the server and moved the document root to /var/www/sites/mySite per the recommendation in the thread, however I am not able to get any .pl scripts to run other than the perltest.pl that is part of the walk through here: [http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.htm]("http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html") 

I have run chmod for each file in the cgi-bin, and even placed a regular html file in the cgi-bin yet nothing so far. Any suggestions would be appreciated and  only minimally scoffed at \\:D/

Well, I rebooted due to a monitor freeze, and now Lo and Behold! Everything seems to be working!

---

