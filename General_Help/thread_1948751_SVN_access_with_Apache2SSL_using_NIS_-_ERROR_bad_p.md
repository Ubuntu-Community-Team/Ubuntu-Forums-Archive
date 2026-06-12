---
title: "SVN access with Apache2/SSL using NIS - ERROR: bad password"
date: 2012-03-28
forum: General Help
---

### Post by tbeavers on 2012-03-28
Greetings,

I have been pulling my hair out trying to get this configuration to work properly, so any help for this noob will be gratefully appreciated.

I am using Ubuntu 11.10 server with Apache2 and SSL. I have NIS configured and can successfully login to the server with an NIS user, so I know NIS is functioning correctly.

I am also able to successfully configure and access SVN using the authz configuration, but when I try to configure for access using Apache2::AuthenNIS, I keep getting "bad password" error in the Apache error.log, which leads me to believe I am almost there, but I am probably just missing something simple with my configs.

Here is a copy of my dav_svn.conf file, which seems to be correct based on everything I have found through Google:

<Location /svn>
DAV svn
SVNParentPath /var/www/svn
SVNListParentPath on
SSLRequireSSL
AuthType Basic
AuthName "Subversion Repository Login"
PerlAuthenHandler Apache2::AuthenNIS
PerlSetVar AllowAlternateAuth no
AuthzSVNAccessFile /etc/apache2/dav_svn.authz
Require valid-user
LimitXMLRequestBody 0
</Location>

...and here is a copy of my dav_svn.authz file:

[groups]
cmteam = beavte01,tbeavers,sancmo01,salech01,matthysa
testteam = testuser

[/]
* = r

[base:/trunk]
@testteam = r
@cmteam = r

[myrepo:/trunk]
@testteam = r
@cmteam = rw

[myrepo2:/trunk]
@testteam = r
@cmteam = rw

========

I am at a total loss here, as everything seems to be configured correctly, so any help will definitely be appreciated!

Thanks in advance!

---

