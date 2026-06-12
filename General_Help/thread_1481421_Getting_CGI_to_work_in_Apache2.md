---
title: "Getting CGI to work in Apache2"
date: 2010-05-12
forum: General Help
---

### Post by h4x0rmx on 2010-05-12
I'm running 10.04 with Apache2/PHP5.x
I wanted to test some basic cgi scripts, but my browser is displaying the code (#!...)
If I run the scripts on the console, they work fine so CGI is not the problem, it's apache.
To install the CGI module I ran 
sudo apt-get install libapache2-mod-perl2
with no problems.
By the way, I installed Apache through apt-get instead of doing it manually, but it seems that the installation divides the conf file in different parts, so the regular apache2.conf has this:

```
# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf
``````
# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
```under **/etc/apache2/mods-enabled/** there's a file (or shortcut to a file) called **cgi.load** which contains this one line:
```
LoadModule cgi_module /usr/lib/apache2/modules/mod_cgi.so
```**mod_cgi.so** does exist.

I can't figure out what I need to do to get CGI working on my server.
Any help?
I will really appreciate it!

---

### Post by cdenley on 2010-05-12
It should work out-of-the-box.
```

echo -e '#!/usr/bin/perl\nprint "Content-type: text/plain\\n\\n";\nprint "It works!\\n";'|sudo tee /usr/lib/cgi-bin/test.pl
sudo chmod 755 /usr/lib/cgi-bin/test.pl
echo -e "GET /cgi-bin/test.pl HTTP/1.0\n"|nc -q 1 127.0.0.1 80

```

---

### Post by gzarkadas on 2010-05-12
Check that your **httpd.conf** has the line:
```

AddHandler cgi-script .cgi

```(or .pl if you use perl scripts)

Also your site configuration file (inside sites-available) has the lines:
```

[B]ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
[/B]    AllowOverride None
    Options **+ExecCGI -MultiViews** +SymLinksIfOwnerMatch
    ...
</Directory>

```The important settings are with bold; the other are depending on your config, so they maybe (or need to be) different. Also the directory entry should have Allow and Deny options.

I don't use Perl as cgi, so things may need to be different for your case; try and see if they work for you.

---

### Post by cdenley on 2010-05-12
> **gzarkadas said:**
> Check that your **httpd.conf** has the line:
```

AddHandler cgi-script .cgi

```(or .pl if you use perl scripts)

Also your site configuration file (inside sites-available) has the lines:
```

[B]ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
[/B]    AllowOverride None
    Options **+ExecCGI -MultiViews** +SymLinksIfOwnerMatch
    ...
</Directory>

```The important settings are with bold; the other are depending on your config, so they maybe (or need to be) different. Also the directory entry should have Allow and Deny options.

I don't use Perl as cgi, so things may need to be different for your case; try and see if they work for you.

The file httpd.conf is not used in ubuntu.

---

### Post by h4x0rmx on 2010-05-12
@cdenley
this is what I get

```
$ echo -e '#!/usr/bin/perl\nprint "Content-type: text/html\\n\\n";\nprint "Hello, world!\\n";'|sudo tee /usr/lib/cgi-bin/test.pl
[sudo] password for h4x0r: 
#!/usr/bin/perl
print "Content-type: text/html\n\n";
print "Hello, world!\n";
```

@gzarkadas
like cdenley said, that file is empty

---

### Post by gzarkadas on 2010-05-12
> **cdenley said:**
> The file httpd.conf is not used in ubuntu.

It is empty, because this is where user settings are meant to be placed (from the Apache docs), but nobody forbids you to use it. And it works; that's how I have set up viewvc to browse my local cvs.

---

### Post by h4x0rmx on 2010-05-12
> **gzarkadas said:**
> It is empty, because this is where user settings are meant to be placed (from the Apache docs), but nobody forbids you to use it. And it works; that's how I have set up viewvc to browse my local cvs.

So, is it here where I should add the handler?
Should it be in some other conf file?
Do my cgi scripts need certain permissions to run?

---

### Post by bredman on 2010-05-12
If Apache displays the contents of a file, it is probably because Apache thinks that the file is not executable.

Use the command
ls -l <filename>
and check if an x shows for the file.

Post the results of the command if you don't know what you are doing.

---

### Post by cdenley on 2010-05-12
> **h4x0rmx said:**
> @cdenley
this is what I get

```
$ echo -e '#!/usr/bin/perl\nprint "Content-type: text/html\\n\\n";\nprint "Hello, world!\\n";'|sudo tee /usr/lib/cgi-bin/test.pl
[sudo] password for h4x0r: 
#!/usr/bin/perl
print "Content-type: text/html\n\n";
print "Hello, world!\n";
```


Well, you ran the first command. I was more interested in the output from the third after changing permissions with the second.

---

### Post by cdenley on 2010-05-12
> **h4x0rmx said:**
> So, is it here where I should add the handler?
Should it be in some other conf file?
Do my cgi scripts need certain permissions to run?

You don't need any handler for cgi with a scriptalias. If you wanted to be able to place CGI scripts anywhere, though, uncomment the handler in /etc/apache2/mods-available/mime.conf.

```
#
# AddHandler allows you to map certain file extensions to "handlers":
# actions unrelated to filetype. These can be either built into the server
# or added with the Action directive (see below)
#
# To use CGI scripts outside of ScriptAliased directories:
# (You will also need to add "ExecCGI" to the "Options" directive.)
#
#AddHandler cgi-script .cgi
```

---

### Post by h4x0rmx on 2010-05-12
@bredman
I get
$ls -l hello.cgi 
-rwxr-xr-x 1 h4x0r h4x0r 148 2006-09-08 12:35 hello.cgi

@cdenley
I'm storing my cgis inside /var/www/cgi
where /var/www/ is the root dir for Apache

Do I need to move them somewhere else? or should I comment the line you mentioned in mime.conf?

[Sorry! I'm a little confused]

---

### Post by cdenley on 2010-05-12
> **h4x0rmx said:**
> @bredman
I get
$ls -l hello.cgi 
-rwxr-xr-x 1 h4x0r h4x0r 148 2006-09-08 12:35 hello.cgi

@cdenley
I'm storing my cgis inside /var/www/cgi
where /var/www/ is the root dir for Apache

Do I need to move them somewhere else? or should I comment the line you mentioned in mime.conf?

[Sorry! I'm a little confused]

It depends on your vhost configuration. On the default vhost, by default, /usr/lib/cgi-bin is defined as a scriptalias, so you can place cgi scripts there. If you want to place cgi scripts in directories which aren't defined as a scriptalias, then you need to uncomment the line I mentioned.

---

### Post by h4x0rmx on 2010-05-12
> **cdenley said:**
> It depends on your vhost configuration. On the default vhost, by default, /usr/lib/cgi-bin is defined as a scriptalias, so you can place cgi scripts there. If you want to place cgi scripts in directories which aren't defined as a scriptalias, then you need to uncomment the line I mentioned.

[@cdenley]("http://ubuntuforums.org/member.php?u=204457")
I did uncomment that line and I get a 403 Forbidden error, which I'd think is better than displaying the content of the file.
I tried to change the permissions of the directory and file, but it didn't work.
I tried:
```
$ chmod a+rx ./cgi/
$ chmod a+rx ./cgi/*
$ chmod a+rx ./cgi/hello.cgi 
$ sudo chown -R h4x0r /var/www/cgi/hello.cgi 

```
Would you guys know how to solve this?
I appreciate your help!

---

### Post by h4x0rmx on 2010-05-12
I took a look at the Apache logs and I found this:
```

[Wed May 12 00:00:00 2010] [error] [client 127.0.0.1] Options ExecCGI is off in this directory: /var/www/cgi/hello.cgi
```

So I guess I have to add a <Directory> entry, but where? I've never done it, so I'm not sure what info goes into that... is this what I have to do?

---

### Post by cdenley on 2010-05-12
> **h4x0rmx said:**
> I took a look at the Apache logs and I found this:
```

[Wed May 12 00:00:00 2010] [error] [client 127.0.0.1] Options ExecCGI is off in this directory: /var/www/cgi/hello.cgi
```

So I guess I have to add a <Directory> entry, but where? I've never done it, so I'm not sure what info goes into that... is this what I have to do?

Yes, or modify the options on an existing one. Either that, or use /usr/lib/cgi-bin which already has ExecCGI enabled. Post your existing vhost configuration, and we can tell you what to change. By default, this would be /etc/apache2/sites-available/default.

---

### Post by h4x0rmx on 2010-05-12
I renamed the /cgi/ folder to /cgi-bin/ and had no luck.
This is my /etc/apache2/sites-enabled/000-default file:

```
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

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    # I added this just to see if it worked
    ScriptAlias /cgi/ /usr/lib/cgi-bin/
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
```

---

### Post by WorMzy on 2010-05-12
You might need to restart apache for any changes to take effect: ```
sudo /etc/init.d/apache2 restart
```

---

### Post by h4x0rmx on 2010-05-12
> **WorMzy said:**
> You might need to restart apache for any changes to take effect: ```
sudo /etc/init.d/apache2 restart
```

I did restart it! :)

I now get a Not Found error when tyring to go to [http://localhost/cgi/hello.cgi](http://localhost/cgi/hello.cgi)
and a 403 Forbidden when trying to go to [http://localhost/cgi/](http://localhost/cgi/)

Error log:

```
[Wed May 12 00:00:00 2010] [error] [client 127.0.0.1] script not found or unable to stat: /usr/lib/cgi-bin/hello.cgi
[Wed May 12 00:00:00 2010] [error] [client 127.0.0.1] attempt to invoke directory as script: /usr/lib/cgi-bin/
```

---

### Post by WorMzy on 2010-05-12
Well, that's a good sign. I can't access my /cgi-bin folder either, so it looks like it's at least treating your /cgi directory in the same manner as a cgi-bin directory. I think the problem now is the script itself.

Try copying this to an empty file in your /cgi directory:
```
#! /usr/bin/perl
use CGI;
my $q=new CGI;
print $q->header();
print $q->start_html(-title=>'Test',-BGCOLOR=>'#AAAAAA');
```
Name it test.cgi or something, then try opening it in your webbrowser. It should make a blank page with the title "Test" and a grey background colour.

If that works, there's a problem with your script.

---

### Post by h4x0rmx on 2010-05-12
> **WorMzy said:**
> Well, that's a good sign. I can't access my /cgi-bin folder either, so it looks like it's at least treating your /cgi directory in the same manner as a cgi-bin directory. I think the problem now is the script itself.

Try copying this to an empty file in your /cgi directory:
```
#! /usr/bin/perl
use CGI;
my $q=new CGI;
print $q->header();
print $q->start_html(-title=>'Test',-BGCOLOR=>'#AAAAAA');
```Name it test.cgi or something, then try opening it in your webbrowser. It should make a blank page with the title "Test" and a grey background colour.

If that works, there's a problem with your script.

I created the file.  I tried running it in the console, but I had to change the permissions with
```
$ chmod a+rx ./cgi/test.cgi 
```
I can't open the script in the browser, though.
The logs keep saying:
```
[Wed May 12 00:00:00 2010] [error] [client 127.0.0.1] script not found or unable to stat: /usr/lib/cgi-bin/test.cgi
```

---

### Post by h4x0rmx on 2010-05-12
mm... Is it looking for */usr/lib/cgi-bin/test.cgi* instead of */var/www/cgi/test.cgi*???

---

### Post by WorMzy on 2010-05-13
I think that's it. If you change this line in your 000-default file
```
ScriptAlias /cgi/ /usr/lib/cgi-bin/
```
To
```
ScriptAlias /cgi/ /var/www/cgi/
```

Or, if you store the scripts at /usr/lib/cgi-bin it'll work as it is.

---

### Post by h4x0rmx on 2010-05-13
> **WorMzy said:**
> I think that's it. If you change this line in your 000-default file
```
ScriptAlias /cgi/ /usr/lib/cgi-bin/
```To
```
ScriptAlias /cgi/ /var/www/cgi/
```Or, if you store the scripts at /usr/lib/cgi-bin it'll work as it is.

That did it! It works now!

```
    ScriptAlias /cgi/ /var/www/cgi/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>
```

Thank you all for all the help! I appreciate it!

---

