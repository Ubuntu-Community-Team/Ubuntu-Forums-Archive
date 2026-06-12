---
title: "twiki - apache error:  couldn't perform authentication. AuthType not set"
date: 2012-07-26
forum: General Help
---

### Post by clubbing80s on 2012-07-26
Hi. 

I'm trying to get twiki running for some reason the authentication is blocking the loading of images etc. I can't see what I have missed .

In the apache logs I'm seeing .. 
[Thu Jul 26 17:24:03 2012] [crit] [client 192.168.1.1] configuration error:  couldn't perform authentication. AuthType not set!: /pub/TWiki/TWikiDocGraphics/index.gif, referer: [https://twiki.example.combin/view/TWiki/WebHome](https://twiki.example.combin/view/TWiki/WebHome)
[Thu Jul 26 17:24:03 2012] [crit] [client 192.168.1.1] configuration error:  couldn't perform authentication. AuthType not set!: /pub/TWiki/TopMenuSkin/menu-gray-bg.png, referer: [https://twiki.example.cm/bin/view/TWiki/WebHome](https://twiki.example.cm/bin/view/TWiki/WebHome)
[Thu Jul 26 17:24:03 2012] [crit] [client 192.168.1.1] configuration error:  couldn't perform authentication. AuthType not set!: /pub/TWiki/TopMenuSkin/menu-reverse-bg.png, referer: [https://twiki.example.combin/bin/view/TWiki/WebHome](https://twiki.example.combin/bin/view/TWiki/WebHome)


I get with this :

 # Password file for TWiki users
 #       AuthUserFile /home/twiki/public_html/data/.htpasswd
 #       AuthName 'Enter your WikiName: (First name and last name, no space, no dots, capitalized, e.g. JohnSmith)'
 #       AuthType Basic
 #       Require valid-user

and :

##### LDAP
# Basic authentication with LDAP against MS AD
AuthType basic
AuthBasicProvider ldap
AuthzLDAPAuthoritative off
AuthLDAPGroupAttributeIsDN off
AuthLDAPURL "ldap://*.*.*.*:3268 *.*.*.*:3268/DC=ad,DC=example,DC=com?sAMAccountName?sub?(objectClass=*)" NONE
AuthLDAPBindDN "CN=twiki apache,OU=Business Units,DC=ad,DC=example,DC=com"
AuthLDAPBindPassword xxxxxxxxxxxxxx
AuthUserFile /dev/null
AuthName "Restricted Site Authentication [Domain Account] Required"
AuthLDAPGroupAttributeIsDN on
Require valid-user
Order allow,deny
Allow from 127.0.0.1
Satisfy Any
##### end LDAP #####

running  Apache/2.2.16 (Ubuntu) with mod_cgi for twiki. authnz_ldap , auth_basic .
on Ubuntu 10.10 \n \l


So far all I have seen on google suggests missing AuthType basic which I have in place in both configurations.

Thanks

---

### Post by clubbing80s on 2012-07-27
I missed the following :

</Directory>

# This sets the options on the pub directory, which contains attachments and
# other files like CSS stylesheets and icons. AllowOverride None stops a
# user installing a .htaccess file that overrides these options.
# Note that files in pub are *not* protected by TWiki Access Controls,
# so if you want to control access to files attached to topics you need to
# block access to the specific directories same way as the ApacheConfigGenerator
# blocks access to the pub directory of the Trash web
<Directory "/home/twiki/public_html/pub">
    Options None
    AllowOverride None
    Order Allow,Deny
    Allow from all
    Deny from env=blockAccess

    # This line will redefine the mime type for the most common types of scripts
    AddType text/plain .shtml .php .php3 .phtml .phtm .pl .py .cgi

#add an Expires header that is sufficiently in the future that the browser does not even ask if its uptodate
# reducing the load on the server significantly
#IF you can, you should enable this - it _will_ improve your twiki experience, even if you set it to under one day.
# you may need to enable expires_module in your main apache config
#LoadModule expires_module libexec/httpd/mod_expires.so
#AddModule mod_expires.c
#<ifmodule mod_expires.c>
#  <filesmatch "\.(jpg|gif|png|css|js)$">
#       ExpiresActive on
#       ExpiresDefault "access plus 11 days"
#   </filesmatch>
#</ifmodule>

</Directory>

---

