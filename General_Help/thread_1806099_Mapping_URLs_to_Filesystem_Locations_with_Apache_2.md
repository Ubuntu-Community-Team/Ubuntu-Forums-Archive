---
title: "Mapping URLs to Filesystem Locations with Apache 2.2"
date: 2011-07-17
forum: General Help
---

### Post by TimeDistort12 on 2011-07-17
I am trying to map a URL to a file system location.

According to official documentation at [http://httpd.apache.org/docs/2.2/urlmapping.html](http://httpd.apache.org/docs/2.2/urlmapping.html) under 'Files Outside the DocumentRoot', it says:

> On Unix systems, symbolic links can bring other parts of the filesystem under the DocumentRoot. For security reasons, Apache will follow symbolic links only if the Options setting for the relevant directory includes FollowSymLinks or SymLinksIfOwnerMatch.

I have did this, and I can see the directory index, but I cannot see folders which should be visible as I have symbolic links pointing to them, in the directory.

This is the content of .htaccess for the relative directory:

```
Options All
```

Every time the client tries to access it, Apache logs this error:

> [Sun Jul 17 19:23:14 2011] [error] [client 127.0.0.1] client denied by server configuration: /usr/local/apache2/htdocs/203.196.95.35/music/.htaccess

Does anyone know why this problem is occurring?

---

