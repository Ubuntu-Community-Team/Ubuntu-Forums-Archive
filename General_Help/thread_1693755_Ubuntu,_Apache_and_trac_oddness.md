---
title: "Ubuntu, Apache and trac oddness"
date: 2011-02-23
forum: General Help
---

### Post by jon.mithe on 2011-02-23
Hi,

Having a tough time setting up trac with apache on ubuntu.  Get the feeling this is more of an apache or python issue with ubuntu.  Finding hard to chase down because it seems to be failing silently.

So I have ubuntu server 10.10 fresh install.  Onto which I have installed apache2, svn and trac (also git and trac git plugin).

Withing this setup I have used svnadmin to create a "testRepo" and trac-admin to create a "testProj" in the /var/svn/testRepo and /var/trac/testProj

I have configured apache for the svn by creating a svn file in the sites-available and linking it to the sites-enabled.  This works great.

I followed a similar way with trac + mod_python as per places on the interweb.  So creating a trac file in sites-available and linking it across.

However, the trac site does not work and I am just getting 404's.

My svn setup:

```

<VirtualHost *:80>
  ServerName mybox 
  ServerAlias svn
  ServerAdmin my.email@interwebs.com
  DocumentRoot /var/www
  ErrorLog /var/log/apache2/svn.error.log
  TransferLog /var/log/apache2/svn.access.log

  <Location /svn>
    DAV svn
    SVNParentPath /var/svn
    AuthType Basic
    AuthName "Subversion"
    AuthUserFile /etc/apache2/svn
    Require valid-user
  </Location>
</VirtualHost>

```

My trac setup:

```


<VirtualHost *:80>
  ServerName mybox
  ServerAlias trac
  ServerAdmin my.email@interwebs.com
  DocumentRoot /var/www
  ErrorLog /var/log/apache2/trac.error.log
  TransferLog /var/log/apache2/trac.access.log

  <Location /trac>
   SetHandler mod_python
   PythonInterpreter main_interpreter
   PythonHandler trac.web.modpython_frontend
   PythonOption TracEnvParentDir /var/trac
   PythonOption TracUriRoot /trac

   AuthType Basic
   AuthName "Trac Auth"
   AuthUserFile /etc/apache2/svn
   Require valid-user
  </Location>
</VirtualHost>


```

Logging is a little odd. So in /var/log/apache2 

error.log:

```

[Wed Feb 23 14:29:12 2011] [error] python_init: Python version mismatch, expected '2.6.5', found '2.6.6'.
[Wed Feb 23 14:29:12 2011] [error] python_init: Python executable found '/usr/bin/python'.
[Wed Feb 23 14:29:12 2011] [error] python_init: Python path being used '/usr/lib/python2.6/:/usr/lib/python2.6/plat-linux2:/usr/lib/python2.6/lib-tk:/usr/lib/python2.6/lib-old:/usr/lib/python2.6/lib-dynload'.
[Wed Feb 23 14:29:12 2011] [notice] mod_python: Creating 8 session mutexes based on 6 max processes and 25 max threads.
[Wed Feb 23 14:29:12 2011] [notice] mod_python: using mutex_directory /tmp 
[Wed Feb 23 14:29:13 2011] [notice] Apache/2.2.16 (Ubuntu) DAV/2 SVN/1.6.12 mod_python/3.3.1 Python/2.6.6 configured -- resuming normal operations

```

Seems its moaning about the version of python, but also seems to say its ok.  I'm hesitant to guess something may be up here.

Whats weird is when I try to access my site at mybox/trac/testProj, the trac.error.log + trac.access.log is completly empty.  

My svn.access.log is as follows:

```

10.2.67.77 - - [23/Feb/2011:14:32:03 +0000] "GET /trac/testProj HTTP/1.1" 404 236

```

I thought this would have been in the trac.access.log, so I am very consufed its in the svn.access.log

So now I am stuck, for all intents I think it should be working, there are no major errors coming up (bar the 404's :P) that I can trac down, so I'm thinking there is a more fundamental problem in the way I have set the trac / apache config up that I am just not getting, or some oddness with mod_python.

I'm running a fresh ubuntu 10.10 64bit install.

Thanks for any help,
Jon

---

### Post by Doug_M on 2011-02-23
I was just googling for info on the Python error.  I've got a very similar setup to yours.  My logging is fine though.  Maybe you need to have separate ServerName entries for svn and trac and not just different aliases in order for the logging to be separated.

Regards,
Doug

---

### Post by jon.mithe on 2011-02-23
aha, thats (sortof) done the trick.  I removed the svn from enabled sites, and then trac has started to work.

So yeah, looks like my apache config for these 2 sites simultaneously is incorrect, will have a play :P

Thanks very much! So happy to see trac working :P
Jon.

---

### Post by jon.mithe on 2011-02-23
hmm so close, but having trouble.

I can get each site working independently but not together.  Have tried in both files and by defining a mybox server file with both locations in, no luck :/

I feel I am doing something stupid with this apache config.  I'm after the end result of

http://mybox/trac/<trac proj>
http://mybox/svn/<svn repo>

If I change the server names I just get 404's, keeping the server names and changing the alias makes the svn work but not trac. hmm, think my lack of apache understanding is showing through...

I will play some more.  Anyone know what I am doing wrong?

Cheers,
Jon

---

### Post by Doug_M on 2011-02-23
I'm doing svn.example.com and trac.example.com both with ssl instead.  Now I know it is not quite what you want for your setup, but here are my site site configs in case they can help you:

```

<VirtualHost *:443>
    ServerName svn.example.com
    <Location />
        DAV svn
        SVNParentPath /var/svn/svn.example.com
        SVNListParentPath On
        AuthType Basic
        AuthName "svn.example.com"
        AuthUserFile /var/svn/svn.example.com/passwd
        Require valid-user
    </Location>
    CustomLog /var/log/apache2/svn.example.com/access.log combined
    ErrorLog /var/log/apache2/svn.example.com/error.log
    SSLEngine on
    SSLCertificateFile /etc/apache2/ssl/apache.pem
    #  Add this once there is a real (non self-signed) certificate.
    #  SSLCertificateKeyFile /etc/apache2/ssl/server.key
</VirtualHost>

<VirtualHost *:80>
  ServerName svn.example.com
  Redirect / https://svn.example.com/
</VirtualHost>

```
and
```

<VirtualHost *:80>
    ServerName trac.example.com
    Redirect / https://trac.example.com/
</VirtualHost>

<VirtualHost *:443>
    ServerName trac.example.com
    DocumentRoot /var/trac/trac.example.com/
    Alias /trac/ /usr/share/pyshared/trac/htdocs

    <Directory "/usr/share/pyshared/trac/htdocs/">
        Options Indexes MultiViews
        AllowOverride None
        Order allow,deny
        Allow from all
    </Directory>

    <Location />
        SetHandler mod_python
        PythonHandler trac.web.modpython_frontend
        PythonInterpreter main_interpreter
        PythonOption TracEnvParentDir /var/trac/trac.example.com/
        PythonOption TracEnvIndexTemplate /var/trac/trac.example.com/available_projects_template.html
        PythonOption TracUriRoot /
        AuthType Basic
        AuthName "trac.example.com"
        # Use the SVN password file.
        AuthUserFile /var/svn/svn.example.com/passwd
        Require valid-user
    </Location>

    CustomLog /var/log/apache2/trac.example.com/access.log combined
    ErrorLog /var/log/apache2/trac.example.com/error.log
    SSLEngine on
    SSLCertificateFile /etc/apache2/ssl/apache.pem
    # Add this once there is a real (non self-signed) certificate.
    #  SSLCertificateKeyFile /etc/apache2/ssl/server.key
</VirtualHost>

```

---

### Post by jon.mithe on 2011-02-23
Ooo thanks, that looks interesting, may take me a while to set this up.  Yeah, I was hoping to do ssl but thought I'd just get the basics working first, will try and blend your config into mine and see what happens.

Just managed to get hudson set up and playing nice with apache, had to tinker with some args in /etc/defaults to get the reverse proxy + default server hidden. :)

Thanks again!
Jon

---

### Post by jon.mithe on 2011-02-23
nope still stuck :/.  Weird, having what seems to be the same issue.  I can run one of these sites at a time.

Two things I am finding odd:

I specify trac.mybox and svn.mybox but it only ever resolves to [https://mybox/](https://mybox/) (so I can either access trac or svn)

Something I noticed in my error log doing it that way with the ssl 
+ different server names was:


```
[Thu Feb 24 00:24:33 2011] [warn] _default_ VirtualHost overlap on port 443, the first has precedence
```

So it seems something it conflicting / overlapping.

Unsure why / how the trac.devbox and svn.devbox prefixes work, more research required...

I created the ssl .pem with the cn name mybox. (yeah ignoring the .com)

Know where this may be goin wrong?

Thanks,
Jon

---

### Post by jon.mithe on 2011-02-24
Hmm, still having trouble.  I feel there is something small / obvious missing in my understanding about how apache / domains work.

I'm guessing the reason svn.devbox trac.devbox do not resolve is becuase there is nothing my routers DNS to resolve that.  However, I dont understand how these could be pointing to the same server, could see having 2 different servers on different IP's would work.

Odd that I can not get it to work both on http;//mybox/trac, http;//mybox/svn tho.

Any suggestions? I'm at a loss :/

Thanks,
Jon.

---

### Post by jon.mithe on 2011-02-24
ok, seem to have it working now.  I defined both these locations in 1 virtual hosts file.  Which makes sense.  From what I've read to do that how I wanted to in other files I need to configure multiple IP's somehow.

But it works this way good enough for now

---

### Post by jon.mithe on 2011-02-24
Ah, managed to get it working and neatish.  For anyone whos interested, this is my final site config file:

```

<VirtualHost *:443>
        # Server setup, logging + ssl
        ServerName mybox
        ServerAlias mybox
        CustomLog /var/log/apache2/mybox.access.log combined
        ErrorLog /var/log/apache2/mybox.error.log
        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/apache.pem

        # Setup .htaccess for the root of the site
        <Location />
                AuthType Basic
                AuthName "mybox"
                AuthUserFile /etc/apache2/passwords
                Require valid-user
        </Location>

        # Hudson setup - reverse proxy to hook up mybox/hudson to the localhost:8080/hudson
        SSLProxyEngine  On
        SSLProxyMachineCertificateFile /etc/apache2/ssl/apache.pem
        ProxyPass        /hudson  https://localhost:8080/hudson
        ProxyPassReverse /hudson  https://localhost:8080/hudson
        ProxyRequests    Off

        <Proxy https://localhost:8080/hudson*>
                Order deny,allow
                Allow from all
        </Proxy>

        # SVN config
        <Location /svn>
                DAV svn
                SVNParentPath /var/svn/
                SVNListParentPath On
        </Location>

        # Trac config
        Alias /trac/ /usr/share/pyshared/trac/htdocs
        <Directory "/usr/share/pyshared/trac/htdocs/">
                Options Indexes MultiViews
                AllowOverride None
                Order allow,deny
                Allow from all
        </Directory>

        <Location /trac>
                SetHandler mod_python
                PythonHandler trac.web.modpython_frontend
                PythonInterpreter main_interpreter
                PythonOption TracEnvParentDir /var/trac/
                PythonOption TracEnvIndexTemplate /var/trac/available_projects_template.html
                PythonOption TracUriRoot /trac
        </Location>

</VirtualHost>

```

To get hudson working you need to edit the /etc/default/hudson file (then do an /etc/init.d/hudson restart afterwards).  The changes required are:

 * set the HTTP_PORT variable to -1 (disables connecting via http)
 * add a variable HTTPS_PORT=8080 and add --httpsPort=$HTTPS_PORT to the HUDSON_ARGS (enables connecting via https)
 * add a --httpsListenAddress=$LISTEN_ADDRESS to the HUDSON_ARGS (sets the listen address for https)
 * Change the LISTEN_ADDRESS variable to 127.0.0.1 (this is important as it makes the hudson server only available to the local server / hides it away from the outside world.  Apache will do the reverse proxy to access it, i.e. hudson is being completely hidden behind apache + any auth it imposes)

Need to enable some modules for apache, cant remeber exactly, something like python, proxy, ssl + whatever is required for trac and svn.

Think thats all I did...

---

