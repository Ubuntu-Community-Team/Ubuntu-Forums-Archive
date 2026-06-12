---
title: "Confusion regarding cache of archives (9.10)"
date: 2010-02-12
forum: General Help
---

### Post by dln9 on 2010-02-12
Ubuntu 9.10.  

How do package files (*.deb) get into /var/cache/apt/archives/ ?  

Do they go in there at the moment they are downloaded?  Or, only after they are actually installed?  

If I get a package via apt, do they go in there?  If I use APTITUDE, do they go in there?  If I use Synaptic, do they go in there?  

What makes them be deleted from there?  If I remove a package - whether via apt, APTITUDE, or SYNAPTIC - does it get deleted from there?  

If I use a tool like aptoncd to rebuild missing packages for currently installed packages, would it cause a problem if I put the rebuilt packages in there?  

If I download and install a package from a web site, would it cause a problem if I put the package file in there?

---

### Post by IcarusR on 2010-02-12
To start with your last question. No you can not put downloaded files there as user does not have 'permissions' to write to that directory. 
Why not create directory debs or downloads in your home directory for this.

I believe the files stay there till either you do a 'Mark for complete removal' in synaptic. Or from terminal 'sudo apt-get purge xyz-package' 'sudo apt-get clean'

For all apt-get options see the manual page..

```
man apt-get
```

Same for aptitude.

```
man aptitude
```

All linux commands have a manual page accessed in this way.

I think files are downloaded to /var/cache/apt/archives/

---

