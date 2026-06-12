---
title: "Apache2, mod_perl and PERL5LIB"
date: 2010-03-13
forum: General Help
---

### Post by Japhering on 2010-03-13
I have basics working,  apache is serving 3 different websites, 2 of which are being served correctly.  The 3rd being the problem.

The 3rd uses a collection of perl modules that live if their own directory.  In theory, I should be able to set  and export PERL5LIB to added the appropriate directory to the perl path as seen by mod_perl.

And indeed, when I  set and export PERL5LIB  and then execute  perl -V  I see the correct paths.

The issue I'm having is that when I set PERL5LIB in either the root shell I'm starting apache2 from or attempt to set in by changing /etc/init.d/apache2 ... the additional paths are not present as my server instance pitches the perl compile failure to the logs.

Karmic,  apache2  2.2.12ubuntu2.2, libapache2-mod-perl2  2.0.4-5ubuntu1, perl  5.10.0-24ubuntu4

---

### Post by jamb on 2010-06-14
I have a similar experience.
Please show me your loaded apache modules with
```
apache2 -t -D DUMP_MODULES

```

---

### Post by Japhering on 2010-06-14
> **jamb said:**
> I have a similar experience.
Please show me your loaded apache modules with
```
apache2 -t -D DUMP_MODULES

```


Fails miserably when executed on my machine

envvars contains
```

export  APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data

```which  is referenced by apache2.conf
```

User ${APACHE_RUN_USER}
Group  ${APACHE_RUN_GROUP}

```which is defined in /etc/passwd  and /etc/group
```

www-data:x:33:33:www-data:/var/www:/bin/sh

www-data:x:33:mhm

``````

apache2  -t -D DUMP_MODULES

produces

apache2: bad user name  ${APACHE_RUN_USER}


```

---

### Post by jamb on 2010-06-17
See my last post below, then retry this again.

Hmmm...try:
```
apache2 -h
```
This *should* present meaningful alternatives. It does works on my server but it runs Gutsy 7.10 (not Karmic)
Here is my outputs, and it's good to have around when looking at Apache2 documentation.
```

apache2 -t -D DUMP_MODULES
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_prefork_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 setenvif_module (shared)
 status_module (shared)
Syntax OK

```

To continue the testing.
First edit your /etc/apache2/sites-available/<configuration-file>
Add to your virtual host:
```

SetEnv PERL5LIB /path/to/your/locallib

```

Also in the same file,
ensure you have a directory stanza to enable perl execution with
```

<Directory /directory/were/you/have/scripts>
Options +ExecCGI
SetHandler cgi-script
</Directory>

```

 
Here is short perl test script to test 'SetEnv' and what Apache pass along to the script.
```

#!/usr/bin/perl -w
use CGI qw(:standard);
print header ;
print "PERL5LIB is: $ENV{PERL5LIB}\n" ; 
print "Apache can read: $ENV{PERL5LIB}\n";
print end_html ;

```

Ensure that your script can execut and load modules (eg. your own MyModule::Test) with a line in the beginning of a test script like so
> 
use lib /path/to/your/locallib ;
use Mymodule::Test ;


There are some bug details on launchpad related to APACHE_RUN_USER/APACHE_RUN_GROUP.

Good luck.
PS I have had no sucess using Apache2 'PassEnv'.

---

### Post by jamb on 2010-06-19
This is a bug and should have been corrected from Intrepid (8.10).
Try with this:> 
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data

Works on my Karmic, and Gutsy 7.10 does not need this, and /etc/apache2/envvars is empty on Gutsy, and my Karmic 'envvars' is same as yours (aka I also have these stanzas).
Also note that my Karmic came from an upgrade from Jaunty 9.04 to Karmic 9.10 in other words not a fresh Karmic install - if that matters.

---

