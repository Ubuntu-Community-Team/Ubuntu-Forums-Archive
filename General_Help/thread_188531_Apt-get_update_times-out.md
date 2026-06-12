---
title: "Apt-get update times-out"
date: 2006-06-04
forum: General Help
---

### Post by phoenix_1983 on 2006-06-04
Hi Everyone,

I'm trying to get access to the multiverse and universe repositories.

I've got the following Sources.list:

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## MAIN REPOSITORIES
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PROPOSED REPOSITORY
deb http://us.archive.ubuntu.com/ubuntu dapper-proposed main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free

## SEVEAS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://mirror.ubuntulinux.nl/ dapper-seveas all

# CIPHERFUNK REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

## WINE REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
Err http://security.ubuntu.com dapper-security Release.gpg                                                                                             n  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com dapper Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://www.beerorkid.com dapper Release.gpg
  Could not connect to www.beerorkid.com:80 (1.0.0.0), connection timed out
Err http://mirror.ubuntulinux.nl dapper-seveas Release.gpg
  Could not connect to mirror.ubuntulinux.nl:80 (1.0.0.0), connection timed out
Err http://xgl.compiz.info dapper Release.gpg
  Could not connect to xgl.compiz.info:80 (1.0.0.0), connection timed out
Err ftp://cipherfunk.org dapper Release.gpg
  Could not connect to cipherfunk.org:21 (1.0.0.0), connection timed out
Err http://deb.opera.com etch Release.gpg
  Could not connect to deb.opera.com:80 (1.0.0.0), connection timed out
Err http://packages.freecontrib.org dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Err http://wine.budgetdedicated.com dapper Release.gpg
  Could not connect to wine.budgetdedicated.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
deb http://wine.budgetdedicated.com/apt dapper main

## OPERA REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://deb.opera.com/opera/ etch non-free

## XGL/COMPIZ REPOSITORIES (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

## DEBIAN REPOSITORIES (Unsupported.  May contain illegal packages.  Use at own risk.)
## deb ftp://ftp.nerim.net/debian-marillat/ etch main
## deb ftp://ftp.nerim.net/debian-marillat/ sid main
## deb ftp://ftp.nerim.net/debian-marillat/ sarge main
```

However,  when i run "sudo apt-get update"  I get the following messages
```

Err http://security.ubuntu.com dapper-security Release.gpg                                                                                             n  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com dapper Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://www.beerorkid.com dapper Release.gpg
  Could not connect to www.beerorkid.com:80 (1.0.0.0), connection timed out
Err http://mirror.ubuntulinux.nl dapper-seveas Release.gpg
  Could not connect to mirror.ubuntulinux.nl:80 (1.0.0.0), connection timed out
Err http://xgl.compiz.info dapper Release.gpg
  Could not connect to xgl.compiz.info:80 (1.0.0.0), connection timed out
Err ftp://cipherfunk.org dapper Release.gpg
  Could not connect to cipherfunk.org:21 (1.0.0.0), connection timed out
Err http://deb.opera.com etch Release.gpg
  Could not connect to deb.opera.com:80 (1.0.0.0), connection timed out
Err http://packages.freecontrib.org dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Err http://wine.budgetdedicated.com dapper Release.gpg
  Could not connect to wine.budgetdedicated.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
```

I did a fresh install of Dapper and had a problem with using IPV6 so i disabled that so that browsing works.

I also have the same issue if i try to download automatix with apt-get

Any help would be appreciated.

Cheers.

---

### Post by blackjack6.21.91 on 2006-06-04
Delete everything in your sources.list under wine except the part

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

and see if that helps.  If nothing your error should be alot shorter :)

---

### Post by phoenix_1983 on 2006-06-04
[QUOTE=blackjack6.21.91]Delete everything in your sources.list under wine except the part

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

and see if that helps.  If nothing your error should be alot shorter :)[/QUOTE]

LOL... ok so maybe that was a little bit of a posting error.....

however... the problem is still persisting.....

---

