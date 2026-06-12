---
title: "Unrecognized URL scheme for ''"
date: 2012-03-21
forum: General Help
---

### Post by xxsawer on 2012-03-21
Hello, I have folloving problem.
I am trying to run svn status -u command in project root directory, but I am getting

```
Unrecognized URL scheme for ''
```Strange is, there is no url inside the quotes...
I found similar thread here
[http://ubuntuforums.org/showthread.php?t=947848](http://ubuntuforums.org/showthread.php?t=947848)
but I think my case is different.
Can anybody help me?

```

svn --version
svn, version 1.5.7 (r36142)
   compiled Aug 10 2009, 14:48:45

Copyright (C) 2000-2008 CollabNet.
Subversion is open source software, see http://subversion.tigris.org/
This product includes software developed by CollabNet (http://www.Collab.Net/).

The following repository access (RA) modules are available:

* ra_neon : Module for accessing a repository via WebDAV protocol using Neon.
  - handles 'http' scheme
  - handles 'https' scheme
* ra_svn : Module for accessing a repository using the svn network protocol.
  - with Cyrus SASL authentication
  - handles 'svn' scheme
* ra_local : Module for accessing a repository on local disk.
  - handles 'file' scheme

``````

type -a svn
svn is /usr/bin/svn
svn is /usr/bin/X11/svn
svn is /usr/bin/X11/svn
svn is /usr/bin/X11/svn

```

---

