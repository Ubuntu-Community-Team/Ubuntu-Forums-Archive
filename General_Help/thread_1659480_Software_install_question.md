---
title: "Software install question"
date: 2011-01-04
forum: General Help
---

### Post by Nick Hopton on 2011-01-04
New to the Ubuntu way of doing things. I have installed PostgreSQL and PostGIS, but not using the package manager. However, I now wish to install 'osm2pgsql'. If I try to do this using the package manager it tells me that I must also install PostgreSQL and PostGIS (older versions that I do not wish to install).

I think I could install 'osm2pgsql' by going something like this from a terminal:

sudo apt-get osm2pgsql

But my question is, if I do this will it install just 'osm2pgsql' or will it also install the other software that I do not want?

Regards, Nick.

---

### Post by nomko on 2011-01-04
Which versions did you installed and which versions will be installed by the package manager? Can you put that here.

---

### Post by Nick Hopton on 2011-01-04
> **nomko said:**
> Which versions did you installed and which versions will be installed by the package manager?
I installed PostgreSQL 9.0 (amd64), which I obtained from the Refractions web site. The package manager would have me install Version 8.4.

The thing is that I have a good, configured and working PostgreSQL/PostGIS installation, all I want to do now is install 'osm2pgsql' (without having to install PostgreSQL/PostGIS again).

Regards, Nick.

---

### Post by nomko on 2011-01-04
Wel, this is the issue here: 
PostgreSQL and PostGIS are dependencies of osm2pgsql. So, if you want to install osm2pgsql, then synaptic automaticly "advise" you to install all the necessary dependencies. Without those, the "main" program won't even run. 
 
What you can do is backup the configuration files and install osm2pgsql with the proposed dependencies and see what happens. Normally if a newer version is installed, the newer version will be left alone and not written over by some older version (is my experience).

---

### Post by oldos2er on 2011-01-04
I would try ```
sudo apt-get install osm2pgsql --ignore-depends --no-install-recommends
```

---

### Post by Nick Hopton on 2011-01-05
Thanks to all for the suggestions. In the end I got round the problem by setting the package manager properties to exclude 'recommended'. I'm only a learner and your advice will noted and no doubt acted upon in times to come. In particular

'sudo apt-get install osm2pgsql --ignore-depends --no-install-recommends'

looks as if it will be very useful.

Regards, Nick.

---

