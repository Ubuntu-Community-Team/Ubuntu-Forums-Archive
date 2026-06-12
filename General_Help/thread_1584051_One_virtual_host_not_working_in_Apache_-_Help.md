---
title: "One virtual host not working in Apache - Help"
date: 2010-09-28
forum: General Help
---

### Post by seattle vic on 2010-09-28
I've been trying to get virtual hosts to work in apache2, and it is working except for a new domain that I just set up through godaddy. Two other domains work fine and I can direct the inputs to simple index.html files in their respective directories. However the domain nwnewday.com just goes to the first host location in the default file, which is victorycat.com. It's almost like apache can't see the domain name.

Here's what I have in sites-available/default:
---------------------------------------------------------

<VirtualHost *:80> #This works fine
ServerName victorycat.com
DocumentRoot /var/www/victorycat
ServerAlias [www.victorycat.com](www.victorycat.com)
</VirtualHost>

<VirtualHost *:80> #This works fine
ServerName retire2soon.com
DocumentRoot /var/www/retire2soon
ServerAlias [www.retire2soon.com](www.retire2soon.com)
</VirtualHost>

<VirtualHost *:80> #This does not work (ie, does not go to /var/www/nwnewday)
ServerName nwnewday.com
DocumentRoot /var/www/nwnewday
ServerAlias [www.nwnewday.com](www.nwnewday.com)
</VirtualHost>

<VirtualHost *:80> #This also does not work
ServerName picasso.nwnewday.com
DocumentRoot /var/www/picasso
ServerAlias [www.picasso.nwnewday.com](www.picasso.nwnewday.com)
</VirtualHost>



ErrorLog ${APACHE_LOG_DIR}/error.log

# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn

CustomLog ${APACHE_LOG_DIR}/access.log combined
-----------------------------------------------------------

I've checked the error log file and get no clues.

Any ideas would be appreciated as I've been working on this for two days and can't figure out what could be wrong.  It seems like it should work.

---

### Post by seattle vic on 2010-09-29
The problem was that godaddy routes the host request through their servers and as a result the host header field "hosts" contained my ip rather than the host name, which is what the apache virtual host file was looking for.  There was another field called "referer" that did have the host name sought, but apache didn't look at it.

After some rooting around on the godaddy site, I found the DNS manager and simply forwarded directly to my ip, and the host name field now contains the name of the host.

A plus is that when I finally figured out I had to look at the host header, it gave me an excuse to learn how to use netcat (nc), which turns out is "really" simple and effective.

---

