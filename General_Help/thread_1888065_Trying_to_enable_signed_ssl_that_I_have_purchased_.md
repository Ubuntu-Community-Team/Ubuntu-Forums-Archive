---
title: "Trying to enable signed ssl that I have purchased from GeoTrust"
date: 2011-11-28
forum: General Help
---

### Post by bignixs on 2011-11-28
I had it set up on my old host's apache server and that is where I bought it but I am now trying to move to my home server, I copied the csr, privatekey, certificate that they provided and I also added the ca-bundle(intermediate.crt) that was emailed to me. It does not work and I am not sure where I am going wrong. I want to point my site [www.5-on-it.com]("http://www.5-on-it.com") to my static ip of my server but the ssl does not work last time I changed the A records in my host DNS settings.


**Here is how I have it configured:**

/etc/apache2/sites-available/5-on-it.com:

```
<VirtualHost *:80>

        ServerAdmin support@5-on-it.com
        ServerName 5-on-it.com
        ServerAlias *5-on-it.com
        DocumentRoot /var/www/5-on-it.com

    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/5-on-it.com/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
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


```/etc/apache2/sites-available/default-ssl:

```
<IfModule mod_ssl.c>
<VirtualHost *:443>
    ServerAdmin admin@localhost.com
        ServerName www.5-on-it.com
        ServerAlias *.5-on-it.com
    DocumentRoot /var/www/5-on-it.com
        ServerPath /5-on-it.com
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/5-on-it.com/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
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


    ErrorLog ${APACHE_LOG_DIR}/error.log


    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

    #   SSL Engine Switch:
    #   Enable/Disable SSL for this virtual host.
    SSLEngine on
        SSLProtocol all

    #   A self-signed (snakeoil) certificate can be created by installing
    #   the ssl-cert package. See
    #   /usr/share/doc/apache2.2-common/README.Debian.gz for more info.
    #   If both key and certificate are stored in the same file, only the
    #   SSLCertificateFile directive is needed.
    SSLCertificateFile    /etc/ssl/certs/www.5-on-it.com.crt
    SSLCertificateKeyFile /etc/ssl/private/www.5-on-it.com.key

    #   Server Certificate Chain:
    #   Point SSLCertificateChainFile at a file containing the
    #   concatenation of PEM encoded CA certificates which form the
    #   certificate chain for the server certificate. Alternatively
    #   the referenced file can be the same as SSLCertificateFile

    #   when the CA certificates are directly appended to the server
    #   certificate for convinience.
    SSLCertificateChainFile /etc/ssl/certs/intermediate.crt

    #   Certificate Authority (CA):
    #   Set the CA certificate verification path where to find CA
    #   certificates for client authentication or alternatively one
    #   huge file containing all of them (file must be PEM encoded)
    #   Note: Inside SSLCACertificatePath you need hash symlinks
    #         to point to the certificate files. Use the provided
    #         Makefile to update the hash symlinks after changes.
    SSLCACertificatePath /etc/ssl/certs/
    SSLCACertificateFile /etc/ssl/certs/intermediate.crt

    #   Certificate Revocation Lists (CRL):
    #   Set the CA revocation path where to find CA CRLs for client
    #   authentication or alternatively one huge file containing all
    #   of them (file must be PEM encoded)
    #   Note: Inside SSLCARevocationPath you need hash symlinks
    #         to point to the certificate files. Use the provided
    #         Makefile to update the hash symlinks after changes.
    #SSLCARevocationPath /etc/apache2/ssl.crl/
    #SSLCARevocationFile /etc/apache2/ssl.crl/ca-bundle.crl

    #   Client Authentication (Type):
    #   Client certificate verification type and depth.  Types are
    #   none, optional, require and optional_no_ca.  Depth is a
    #   number which specifies how deeply to verify the certificate
    #   issuer chain before deciding the certificate is not valid.
    #SSLVerifyClient require
    #SSLVerifyDepth  10

    #   Access Control:
    #   With SSLRequire you can do per-directory access control based
    #   on arbitrary complex boolean expressions containing server
    #   variable checks and other lookup directives.  The syntax is a
    #   mixture between C and Perl.  See the mod_ssl documentation
    #   for more details.
    #<Location />
    #SSLRequire (    %{SSL_CIPHER} !~ m/^(EXP|NULL)/ \
    #            and %{SSL_CLIENT_S_DN_O} eq "Snake Oil, Ltd." \
    #            and %{SSL_CLIENT_S_DN_OU} in {"Staff", "CA", "Dev"} \
    #            and %{TIME_WDAY} >= 1 and %{TIME_WDAY} <= 5 \
    #            and %{TIME_HOUR} >= 8 and %{TIME_HOUR} <= 20       ) \
    #           or %{REMOTE_ADDR} =~ m/^192\.76\.162\.[0-9]+$/
    #</Location>

    #   SSL Engine Options:
    #   Set various options for the SSL engine.
    #   o FakeBasicAuth:
    #     Translate the client X.509 into a Basic Authorisation.  This means that
    #     the standard Auth/DBMAuth methods can be used for access control.  The
    #     user name is the `one line' version of the client's X.509 certificate.
    #     Note that no password is obtained from the user. Every entry in the user
    #     file needs this password: `xxj31ZMTZzkVA'.
    #   o ExportCertData:
    #     This exports two additional environment variables: SSL_CLIENT_CERT and
    #     SSL_SERVER_CERT. These contain the PEM-encoded certificates of the
    #     server (always existing) and the client (only existing when client
    #     authentication is used). This can be used to import the certificates
    #     into CGI scripts.
    #   o StdEnvVars:
    #     This exports the standard SSL/TLS related `SSL_*' environment variables.
    #     Per default this exportation is switched off for performance reasons,
    #     because the extraction step is an expensive operation and is usually
    #     useless for serving static content. So one usually enables the
    #     exportation for CGI and SSI requests only.
    #   o StrictRequire:
    #     This denies access when "SSLRequireSSL" or "SSLRequire" applied even
    #     under a "Satisfy any" situation, i.e. when it applies access is denied
    #     and no other module can change it.
    #   o OptRenegotiate:
    #     This enables optimized SSL connection renegotiation handling when SSL
    #     directives are used in per-directory context.
    #SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
    <FilesMatch "\.(cgi|shtml|phtml|php)$">
        SSLOptions +StdEnvVars
    </FilesMatch>
    <Directory /usr/lib/cgi-bin>
        SSLOptions +StdEnvVars
    </Directory>

    #   SSL Protocol Adjustments:
    #   The safe and default but still SSL/TLS standard compliant shutdown
    #   approach is that mod_ssl sends the close notify alert but doesn't wait for
    #   the close notify alert from client. When you need a different shutdown
    #   approach you can use one of the following variables:
    #   o ssl-unclean-shutdown:
    #     This forces an unclean shutdown when the connection is closed, i.e. no
    #     SSL close notify alert is send or allowed to received.  This violates
    #     the SSL/TLS standard but is needed for some brain-dead browsers. Use
    #     this when you receive I/O errors because of the standard approach where
    #     mod_ssl sends the close notify alert.
    #   o ssl-accurate-shutdown:
    #     This forces an accurate shutdown when the connection is closed, i.e. a
    #     SSL close notify alert is send and mod_ssl waits for the close notify
    #     alert of the client. This is 100% SSL/TLS standard compliant, but in
    #     practice often causes hanging connections with brain-dead browsers. Use
    #     this only for browsers where you know that their SSL implementation
    #     works correctly.
    #   Notice: Most problems of broken clients are also related to the HTTP
    #   keep-alive facility, so you usually additionally want to disable
    #   keep-alive for those clients, too. Use variable "nokeepalive" for this.
    #   Similarly, one has to force some clients to use HTTP/1.0 to workaround
    #   their broken HTTP/1.1 implementation. Use variables "downgrade-1.0" and
    #   "force-response-1.0" for this.
    BrowserMatch "MSIE [2-6]" \
        nokeepalive ssl-unclean-shutdown \
        downgrade-1.0 force-response-1.0
    # MSIE 7 and newer should be able to use keepalive
    BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown

</VirtualHost>
</IfModule>

```/etc/apache2/sites-available/default:

```
<VirtualHost *:80>

        ServerAdmin admin@localhost.com
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

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
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

```**Here are some screens:**

/etc/ssl/

[IMG]http://www.prohosta.com/sslroot.png[/IMG]

/etc/ssl/private/

[IMG]http://www.prohosta.com/privat.png[/IMG]
[IMG]http://prohosta.com/private.png[/IMG]

/etc/ssl/certs/

[IMG]http://www.5-on-it.com/5-on-itcrt.png[/IMG][IMG]http://prohosta.com/5-on-itcrt.png[/IMG]

[IMG]http://www.5-on-it.com/intermediatecrt.png[/IMG][IMG]http://prohosta.com/intermediatcrt.png[/IMG]

Any Help is Appreciated!

---

### Post by bignixs on 2011-11-28
Does any one have any suggestions or somewhere else I can ask for help? Did I post in the wrong section?

---

### Post by synexis on 2011-11-28
Hello,

To start with, do you get an error when you restart Apache? It usually does a good job of hinting at what's not right. If it's working you should see something like:```
 * Restarting web server apache2
 ... waiting .   ...done.
```If not, what's happening that shouldn't be? (e.g., Do you get an HTTP error when you try to access your site via https? What is that error?)

Also, I noticed you posted the contents of  /etc/apache2/sites-available/default-ssl twice, the first defines connections on port 80. I'm assuming this was a mistake in your post, but if not that would be a cause for concern.

Cheers.

---

### Post by bignixs on 2011-11-28
> **synexis said:**
> Hello,

To start with, do you get an error when you restart Apache? It usually does a good job of hinting at what's not right. If it's working you should see something like:```
 * Restarting web server apache2
 ... waiting .   ...done.
```If not, what's happening that shouldn't be? (e.g., Do you get an HTTP error when you try to access your site via https? What is that error?)

Also, I noticed you posted the contents of  /etc/apache2/sites-available/default-ssl twice, the first defines connections on port 80. I'm assuming this was a mistake in your post, but if not that would be a cause for concern.

Cheers.

When I restart apache I get:

...waiting [ ok ]

when I try and access https:// I get

Unable to connect
      
Firefox can't establish a connection to the server at 96.41.82.107.

sorry the first code is of /etc/apache2/sites-available/5-on-it.com

---

### Post by synexis on 2011-11-28
I tried both [https://*example*]("https://%3Ci%3Eexample%3C/i%3E")*.*com/ and [https://www](https://www).*example.*com/ (using your domain), and they work fine for me with a valid trusted SSL connection (I see your logo with a message about site maintenance). Were you trying to access your site via your server IP or "localhost"? Your certificates are specific to the domain name, so that wouldn't work (or at least the connection would not be trusted). Otherwise it seems your issue is related to your own workstation or network.

---

### Post by bignixs on 2011-11-28
> **synexis said:**
> I tried both [https://*example*]("https://%3Ci%3Eexample%3C/i%3E")*.*com/ and [https://www](https://www).*example.*com/ (using your domain), and they work fine for me with a valid trusted SSL connection (I see your logo with a message about site maintenance). Were you trying to access your site via your server IP or "localhost"? Your certificates are specific to the domain name, so that wouldn't work (or at least the connection would not be trusted). Otherwise it seems your issue is related to your own workstation or network.

Yes, I do not currently have the A records pointing to my servers ip which is:

[http://96.41.82.107](http://96.41.82.107)

When I do point it to my servers ip then I can type the domain and access the http:// side but not the https:// side

---

### Post by synexis on 2011-11-28
Sorry, I didn't read your original question very thoroughly.

Firstly, I'm guessing that the cert/key combo you copied is specific to you domain name, so even if you use them to secure your server's IP address, the connection will not be trusted.

If you're okay with that, however, it looks like perhaps your default-ssl configuration is not set up correctly. To test, I would disable that site (e.g., a2dissite default-ssl) and create then enable the following minimal configuration, ruling out some possible problems:

```
<VirtualHost 96.41.82.107:443>
    DocumentRoot /var/www/5-on-it.com

    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/www.5-on-it.com.crt
    SSLCertificateKeyFile /etc/ssl/private/www.5-on-it.com.key
</VirtualHost>
```(and make sure to reload apache)

Then you can add back whatever directives are needed several at a time to determine which ones are preventing the site from loading.

Aside from that, I'm not sure what might be causing the issue. This may be more effectively solved on an Apache forum as I don't think it's specific to Ubuntu.

Best of luck.

---

### Post by bignixs on 2011-11-28
> **synexis said:**
> Sorry, I didn't read your original question very thoroughly.

Firstly, I'm guessing that the cert/key combo you copied is specific to you domain name, so even if you use them to secure your server's IP address, the connection will not be trusted.

If you're okay with that, however, it looks like perhaps your default-ssl configuration is not set up correctly. To test, I would disable that site (e.g., a2dissite default-ssl) and create then enable the following minimal configuration, ruling out some possible problems:

```
<VirtualHost 96.41.82.107:443>
    DocumentRoot /var/www/5-on-it.com

    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/www.5-on-it.com.crt
    SSLCertificateKeyFile /etc/ssl/private/www.5-on-it.com.key
</VirtualHost>
```(and make sure to reload apache)

Then you can add back whatever directives are needed several at a time to determine which ones are preventing the site from loading.

Aside from that, I'm not sure what might be causing the issue. This may be more effectively solved on an Apache forum as I don't think it's specific to Ubuntu.

Best of luck.

What do I save this file as or where do I add it?

Also I have pointed [http://www.5-on-it.com/](http://www.5-on-it.com/) to my servers ip, is everyone able to see it?

[http://www.5-on-it.com/](http://www.5-on-it.com/)

---

### Post by bignixs on 2011-11-29
> **synexis said:**
> Sorry, I didn't read your original question very thoroughly.

Firstly, I'm guessing that the cert/key combo you copied is specific to you domain name, so even if you use them to secure your server's IP address, the connection will not be trusted.

If you're okay with that, however, it looks like perhaps your default-ssl configuration is not set up correctly. To test, I would disable that site (e.g., a2dissite default-ssl) and create then enable the following minimal configuration, ruling out some possible problems:

```
<VirtualHost 96.41.82.107:443>
    DocumentRoot /var/www/5-on-it.com

    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/www.5-on-it.com.crt
    SSLCertificateKeyFile /etc/ssl/private/www.5-on-it.com.key
</VirtualHost>
```(and make sure to reload apache)

Then you can add back whatever directives are needed several at a time to determine which ones are preventing the site from loading.

Aside from that, I'm not sure what might be causing the issue. This may be more effectively solved on an Apache forum as I don't think it's specific to Ubuntu.

Best of luck.

Updated each file one by one with the code you gave but still no success :(

---

