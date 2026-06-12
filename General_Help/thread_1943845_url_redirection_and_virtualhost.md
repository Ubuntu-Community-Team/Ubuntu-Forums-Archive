---
title: "url redirection and virtualhost"
date: 2012-03-20
forum: General Help
---

### Post by eawz9999 on 2012-03-20
**[SIZE="2"]SETUP[/SIZE]**

Ubuntu 11.04 server on desktop running apache2 with several name-based virtualhosts.
All my ports are closed except for port 443(ssl) and 22 (ssh)
Dynamic IP address handled by dyndns for IP updates (ddclient).
Each one of my virtual hosts has a DNS defined at dyndns.
(black hole) is a directory which has hardly any permissions, no subdirectories and a simple index.php that says “Private server”.
This is a generic partial list of my sites-available virtualhosts configuration:


# DEFAULT FOR PORT 443

NameVirtualHost *:443
<IfModule mod_ssl.c>
<VirtualHost *:443>
	
	DocumentRoot /var/www (black hole)

# -----------------------------------------------
# Second virtualhost

<IfModule mod_ssl.c>
<VirtualHost *:443>
	
ServerName myserver.name.com

DocumentRoot /var/www (black hole)

Alias /could-be-complex 	/home/www/mypage
# -----------------------------------------------

# Third, Fourth… etc
# -----------------------------------------------

Default handles:
Any request to my dynamic IP with or without aliases.
Any request to my DNSs without matching /alias.
**[https://myserver.name.com/alias](https://myserver.name.com/alias) (this is correct**).

**[SIZE="2"]Question:[/SIZE]**
To further experiment (_**and learn**_) y purchased a DNS from Register.
On my account there I entered a URL redirection to an account at dyndna. 
The redirection is: new.register.com > [https://myserver.name.com](https://myserver.name.com).
This works fine. I type new.register.com and my apache2 receives this on myserver.name.com.
However when I try to add an alias (new.register.com/alias) my apache2 ignores this alias.
I do not fully understand what is my server receiving. Is the /alias been send in the redirection request?
Thank you, Enrique

---

