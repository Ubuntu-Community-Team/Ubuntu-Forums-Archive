---
title: "apache2 redirect error"
date: 2011-02-08
forum: General Help
---

### Post by spindler on 2011-02-08
I am running Ubuntu 10.04  with a LAMP install.   I am also running several websites using wordpress 3.0.5.

I am having some problems uploading a file to my server from within wordpress.  I first thought the problem was with the permission setting of the directors and folder.   Here is a link to this discussion.

[http://ubuntuforums.org/showthread.php?p=10434020#post10434020](http://ubuntuforums.org/showthread.php?p=10434020#post10434020)

I now believe the problem might be with Apache2.  When i upload a file using wordpress  I get the following error message.

**“Picture.jpg” has failed to upload due to an error**
Unable to create directory /var/www/html/wp-content/uploads/2011/02. Is its parent directory writable by the server?

The reason why it cannot write to the above director is because apache2  is suppose to redirect this request to the correct folder which is    /home/USER/WEBSITE/wp-content/uploads/2011/02.

ONE THING TO CONSIDER:  This is the only problem I am having with wordpress.  I can do a bunch of other tasks with ease such as update plugins, update wordpress, create posts and pages etc.   I just cannot upload a file into the correct directory.

I am not sure what is happening with apache2.  Here is the Virtual host config file.

<VirtualHost *:80>
    ServerAdmin [EMAIL="XXX@XXXX.org"]XXX@XXXX.org[/EMAIL]
    ServerName WEBSITE.org
    ServerAlias *.WEBSITE.org

    DocumentRoot /home/USER/WEBSITE
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /home/USER/WEBSITE>
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
        Allow from 1XX.0.0.0/2XX.0.0.0 ::1/XXX
    </Directory>

</VirtualHost>

Any ideas why Apache2 is not redirecting correctly for this particular request?

Thanks,

Spindler:lolflag:

---

