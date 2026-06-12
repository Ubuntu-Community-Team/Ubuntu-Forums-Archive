---
title: "Looking for 400 ErrorDoc Bad Request"
date: 2011-04-07
forum: General Help
---

### Post by knrobins on 2011-04-07
When trying to access  the SSL port over http

i.e.   [http://hostname:4443](http://hostname:4443)   get the following error page.

**Bad Request**

 Your browser sent a request that this server could not understand.
Reason: You're sp[FONT=Verdana]eaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to[/FONT] access this URL, please.

[INDENT]Hint: [**https://xxxxxxxxxx:4443/**]("https://moses.homeunix.net:4443/")[/INDENT]  Apache/2.2.14 (Ubuntu) Server at xxxxxxxxx Port 4443


I'm not looking for the solution to this,  I know what it is.   What I want to know is where does this page come from.  It doesn't appear to be the standard 

HTTP_BAD_GATEWAY.html.var 

from /usr/share/apache2/error

Is this dynamically generated?  Is it a perl script or PHP that generats html?

Thanks

---

