---
title: "used --ignore-depends because of source install and now dependencies are broken"
date: 2011-06-16
forum: General Help
---

### Post by spike666 on 2011-06-16
Hi

I installed Ruby Enterprise Edition from source on my system and then I installed the latest version of mcollective's .deb distribution using --ignore-depends=ruby and now I can't install or update packages using apt-get.

apt thinks that I don't have ruby installed and I don't want to have 2 versions of it installed on the system. I also tried (on a different, fresh ubuntu install) to install ruby ee's .deb distribution, but since the package name is ruby-enterprise, it doesn't satisfy either the 'ruby' or 'rubygems' dependencies.

Did I go about this the wrong way or am I missing something?

installing mcollective:

```

$ sudo dpkg --ignore-depends=ruby --ignore-depends=rubygems -i mcollective*.deb
(Reading database ... 49761 files and directories currently installed.)
Preparing to replace mcollective 1.2.0-6 (using mcollective_1.2.0-6_all.deb) ...
Unpacking replacement mcollective ...
Preparing to replace mcollective-client 1.2.0-6 (using mcollective-client_1.2.0-6_all.deb) ...
Unpacking replacement mcollective-client ...
Preparing to replace mcollective-common 1.2.0-6 (using mcollective-common_1.2.0-6_all.deb) ...
Unpacking replacement mcollective-common ...
Preparing to replace mcollective-doc 1.2.0-6 (using mcollective-doc_1.2.0-6_all.deb) ...
Unpacking replacement mcollective-doc ...
Setting up mcollective-common (1.2.0-6) ...
Setting up mcollective-doc (1.2.0-6) ...
Setting up mcollective (1.2.0-6) ...
Setting up mcollective-client (1.2.0-6) ...
Processing triggers for ureadahead ...


```

trying to install a new package:

```

$ sudo apt-get install bind9-host
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 bind9-host : Depends: libbind9-60 (= 1:9.7.3.dfsg-1ubuntu2.1) but it is not going to be installed
              Depends: libdns69 (= 1:9.7.3.dfsg-1ubuntu2.1) but it is not going to be installed
              Depends: libisc62 (= 1:9.7.3.dfsg-1ubuntu2.1) but it is not going to be installed
              Depends: libisccfg62 (= 1:9.7.3.dfsg-1ubuntu2.1) but it is not going to be installed
              Depends: liblwres60 (= 1:9.7.3.dfsg-1ubuntu2.1) but it is not going to be installed
              Depends: libxml2 (>= 2.6.27) but it is not going to be installed
 mcollective : Depends: ruby (>= 1.8.1) but it is not going to be installed
 mcollective-client : Depends: ruby (>= 1.8.1) but it is not going to be installed
 mcollective-common : Depends: ruby (>= 1.8.1) but it is not going to be installed
                      Depends: rubygems but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

running apt-get -f install:

```

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libruby1.8 ruby ruby1.8 ruby1.8-dev rubygems rubygems1.8
Suggested packages:
  ri ruby-dev ruby1.8-examples ri1.8 rubygems-doc
The following NEW packages will be installed:
  libruby1.8 ruby ruby1.8 ruby1.8-dev rubygems rubygems1.8
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,643 kB of archives.
After this operation, 11.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
adminis

```

---

### Post by abetterlie on 2011-09-20
I have exactly the same issue, have you come up with a solution yet?

---

