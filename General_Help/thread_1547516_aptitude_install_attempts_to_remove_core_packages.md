---
title: "aptitude install attempts to remove core packages"
date: 2010-08-06
forum: General Help
---

### Post by Stardom on 2010-08-06
Im having an issue with sudo aptitude install. If i attempt to install anything, it says it will remove all of the packages below. On the other hand, if i use the Synaptic Package Manager, it doesn't remove any packages what is going on here? Any ideas? I have added some karmic repositories, but i dont think that should do anything?


 sudo aptitude install libossp-uuid-dev

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  libossp-uuid-dev libossp-uuid16{a} 
The following packages will be REMOVED:
  apache2{u} apache2-mpm-worker{u} apache2-utils{u} apache2.2-bin{u} 
  apache2.2-common{u} cython{u} dpatch{u} gap{u} gap-character-tables{u} 
  gap-core{u} gap-dev{u} gap-doc{u} gap-guava{u} gap-libs{u} 
  gap-online-help{u} gap-prim-groups{u} gap-small-groups{u} 
  gap-trans-groups{u} genus2reduction{u} gfan{u} gfortran{u} 
  gfortran-4.4{u} global{u} gmp-ecm{u} gnuplot{u} gnuplot-nox{u} 
  gnuplot-x11{u} groff{u} ipython{u} lcalc{u} libaccess-bridge-java{u} 
  libaccess-bridge-java-jni{u} libaprutil1-dbd-sqlite3{u} 
  libaprutil1-ldap{u} libblas-dev{u} libboost-python1.40.0{u} 
  libcdd-test{u} libcdd0{u} libdb4.6{u} libdsdp-5.8gf{u} libecm0{u} 
  libflint-1.011{u} libfplll0{u} libgivaro0{u} libglpk0{u} libiml0{u} 
  liblapack-dev{u} liblinbox0{u} libm4ri-0.0.20080521{u} libmpfi0{u} 
  libnetpbm10{u} libntl-5.4.2{u} libopagent1{u} libpari2-gmp{u} 
  libpcre3-dev{u} libpcrecpp0{u} libpolybori-0.5.0-0{u} libpolybori-dev{u} 
  libqd2c2a{u} libreadline5{u} libsingular-3-0-4-3{u} libsingular-dev{u} 
  libsymmetrica-2.0{u} libyaml-0-2{u} libzn-poly-0.8{u} maxima{u} 
  maxima-emacs{u} maxima-share{u} mercurial{u} mercurial-common{u} 
  netpbm{u} oprofile{u} palp{u} pari-extra{u} pari-gp{u} patchutils{u} 
  psutils{u} python-cvxopt{u} python-foolscap{u} python-gd{u} 
  python-gnuplot{u} python-gnutls{u} python-moinmoin{u} python-networkx{u} 
  python-polybori{u} python-processing{u} python-pyasn1{u} 
  python-pygments{u} python-pygraphviz{u} python-rpy{u} 
  python-sqlalchemy{u} python-sympy{u} python-transaction{u} 
  python-twisted{u} python-twisted-conch{u} python-twisted-lore{u} 
  python-twisted-mail{u} python-twisted-news{u} python-twisted-runner{u} 
  python-twisted-web2{u} python-twisted-words{u} python-yaml{u} 
  python-zc.lockfile{u} python-zconfig{u} python-zdaemon{u} python-zodb{u} 
  python-zope.event{u} python-zope.exceptions{u} python-zope.proxy{u} 
  python-zope.testing{u} python2.5{u} python2.5-minimal{u} r-base{u} 
  r-base-core{u} r-base-dev{u} r-base-html{u} r-cran-boot{u} 
  r-cran-class{u} r-cran-cluster{u} r-cran-codetools{u} r-cran-foreign{u} 
  r-cran-kernsmooth{u} r-cran-lattice{u} r-cran-mass{u} r-cran-matrix{u} 
  r-cran-mgcv{u} r-cran-nlme{u} r-cran-nnet{u} r-cran-rpart{u} 
  r-cran-spatial{u} r-cran-survival{u} r-doc-html{u} r-recommended{u} 
  scons{u} singular{u} sqlite3{u} sympow{u} tachyon{u} texlive-latex3{u} 
0 packages upgraded, 2 newly installed, 139 to remove and 1 not upgraded.
Need to get 132kB of archives. After unpacking 479MB will be freed.
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libossp-uuid16 1.6.2-1ubuntu1 [58.5kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libossp-uuid-dev 1.6.2-1ubuntu1 [73.8kB]
Fetched 132kB in 0s (137kB/s)

---

### Post by inameiname on 2010-08-06
That is quite a bit of stuff. I have a feeling it's stuff that it's asking you to remove regardless of what you are installing. 

Try:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

...and see if those same things pop up. 

I always use aptitude and just remove all that it asks as they are no longer required and never have an issue.

---

### Post by oldos2er on 2010-08-06
Are you running Karmic or Lucid? Whichever it is, you need to remove any repositories for Ubuntu versions you're not running.

---

### Post by Stardom on 2010-08-06
Somehow, cleaning it worked and just to be sure i got rid of the karmic repositories! Thanks! Im a little unsure about trusting it because last time it said it wanted to uninstall alot of things i had to reinstall the operating system because it removed a lot of core components.

---

### Post by inameiname on 2010-08-06
I see. Yeah, it can do that sometimes, especially if you are using an upgraded version of Ubuntu, from say Karmic to Lucid. There's often a few stuff left over, and a few others that can screw things up. Not nearly as bad as Windows upgrades though. :P When a new version of Ubuntu comes out I always just start from scratch, so I don't run across too many woes in that sense.

---

