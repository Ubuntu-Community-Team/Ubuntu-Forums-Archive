---
title: "Apache proxy module"
date: 2010-02-01
forum: General Help
---

### Post by kcusscam on 2010-02-01
Hello,

I am trying a release of Ubuntu has have run into a problem that does not make much sense.  I am receiving the following error:

Syntax error on line 20 of /etc/apache2/sites-enabled/portal:
Invalid command 'ProxyHTMLEnable', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!

I believe the modules required for this is  apt-get install libapache2-mod-proxy-html and it shows under the available modules and it was enabled with a2enmod proxy-html.

The line from the config is ProxyHTMLEnable On.
The release is the latest download with updates from, 32bit.

Am I missing something?

Jeremy

---

### Post by t4thfavor on 2010-02-01
you have to enable the modules, try looking in the mods-available folder and see if you missed one.

the command to enable it is a2enmod modulename

good luck.

---

### Post by intargc on 2010-03-14
I'm having this problem now too.

The module is in my mods-enabled directory and according to the apache log file it is actually loading.  However, it is not allowing me to use the directive ProxyHTMLEnable on.  It's saying it's an invalid directive.  I can, however, use any of the other ProxyHTML* directives... but they're all worthless unless I can enable it!

Any ideas?

---

### Post by schworak on 2010-12-19
> **intargc said:**
> I'm having this problem now too.

The module is in my mods-enabled directory and according to the apache log file it is actually loading.  However, it is not allowing me to use the directive ProxyHTMLEnable on.  It's saying it's an invalid directive.  I can, however, use any of the other ProxyHTML* directives... but they're all worthless unless I can enable it!

Any ideas?


Did you ever get it working? I am having the same issue.

---

### Post by zuffi on 2011-06-29
the actual problem is, that the directive "ProxyHTMLEnable" is available with mod-proxy-html 3.1

ubuntu comes with mod-proxy-html 3.0.1 (11.04)

try SetOutputFilter proxy-html

---

