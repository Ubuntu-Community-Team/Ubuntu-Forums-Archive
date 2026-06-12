---
title: "libkrb5-3 and libkrb5support0 packages"
date: 2011-03-24
forum: General Help
---

### Post by mdavidjohnson on 2011-03-24
I'm trying to install pg_config so I can get some simple reports regarding my PostgreSQL 8.4.7 installation.

I downloaded pg_config and its dependencies and tried to install them with the package installer, but it wouldn't go because it seems like something may be wrong with the libkrb5-3 and libkrb5support0 packages - they won't install and the package installer just zips through without reporting missing dependencies or anything. The MD5, SHA1, and SHA256 checksums all match, but they just won't install. 

I downloaded all the packages from the ubuntu [security] repository.

Because my Ubuntu 10.04 (Lucid) machine is not connected to the internet, I download packages to my Windows 7 machine, transfer them across my network to a shared folder on my Ubuntu machine and double-click the package to install.

I&#8217;ve successfully installed postgresql-8.4, apache-2.2.14, php-5.3.2, drupal-6.16, and several other packages and all their dependencies this way without any problems before.

To make sure I wasn&#8217;t having some new problem, I then tried installing libk5crypto3 - it installed fine.

I sent an email to [email]frank@lichtenheld.de[/email] , the repository maintainer, but haven't heard back from him yet.

Has anybody else encountered a problem with these packages?

---

### Post by mdavidjohnson on 2011-03-25
Of some interest may be the fact that I went ahead and connected my Ubuntu machine to the internet. Then I did:

sudo apt-get install pg_config

and now I get:

Couldn't find package pg_config.

Checking the repository at [http://packages.ubuntu.com/lucid/i386/allpackages](http://packages.ubuntu.com/lucid/i386/allpackages) shows that it seems to have disappeared.

Meanwhile, back at the ranch:

sudo apt-get install gimp

worked perfectly.

---

