---
title: "websvn access rights for individual repositories???"
date: 2009-07-31
forum: General Help
---

### Post by Mark20 on 2009-07-31
Hi all,

I've setup SVN, and webSVN in my apache2 server, and I would like to have different access rights for each of my two repositories.  I have tried many configuration changes, but no matter what I do, I can't seem to figure this out.  Does anyone know if this is possible?  I've spent a lot of time trying to get websvn to work, since there is no documentation I've actually been looking at the source code trying to figure this out.  I've looked at the [debian howto]("http://www.howtoforge.com/debian_subversion_websvn"), but it doesn't help.  Any suggestions?

Also - I am using SVN+SSH for authentication whenever users want to access SVN without websvn.  What access file should websvn be using?  Currently I've added this to my /etc/websvn/config.php file:
```

$config->useAuthenticationFile('/etc/passwd', '/var/svn-repos/myRepo');

```

where 'myRepo' is the name of my SVN repository.

---

