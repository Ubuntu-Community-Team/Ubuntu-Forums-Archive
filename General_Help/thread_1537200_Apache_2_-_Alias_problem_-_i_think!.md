---
title: "Apache 2 - Alias problem - i think!"
date: 2010-07-23
forum: General Help
---

### Post by bluntknife on 2010-07-23
Hi,
I am having an odd problem on my Ubuntu 9.10 web server.

I am running Nagios 3 (install using apt) and all is well.  I then followed the instructions for installing pnp4nagios so I can visualise events in graph form.  Following the instructions [here]("http://docs.pnp4nagios.org/pnp-0.6/install") I managed to eventually define the correct paths, configure all the config files that need updating and other than a couple of minor errors that were easily resolved, all seemed to go well.

Now.  I am supposed to be able to resolve [http://localhost/pnp4nagios](http://localhost/pnp4nagios) but this just returns an 'internal server error' from apache2.

Weird thing is, if I create a link from /var/www to the pnp4nagios web files (/usr/local/pnp4nagios/share) I can successfully resolve to [http://localhost/share](http://localhost/share).

BUT, if i name the /var/www link pnp4nagios and try to resolve [http://localhost/pnp4nagios](http://localhost/pnp4nagios) I receive the 'internal server error' message again!

Please can someone offer a solution to my problem as it's driving me mad.  Btw, I need to resolve to pnp4nagios rather than anything else (such as 'share') because other nagios plugins have hard coded that URL.

Many thanks in advance.

---

### Post by bluntknife on 2010-07-23
Fixed it!

Needed to edit /etc/apache2/conf.d/pnp4nagios.conf

Comment out 
> AuthUserFile /usr/local/nagios/etc/htpasswd.users

and replaced it with
> AuthUserFile /etc/nagios3/htpasswd.users

---

### Post by alfp on 2012-03-04
Fix issue for me too

Thanks!

---

