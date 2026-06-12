---
title: "Offline Repository tells me file not found."
date: 2012-06-09
forum: General Help
---

### Post by adelsin on 2012-06-09
Unsure what I did. I removed all other entries out of /etc/apt/sources.list except for my local entry.

```
deb file:///repository/ lucid main restricted multiverse universe
```

It does return errors/warnings with apt-get update or --fix-missing are applied.

I did rebuild the Release.gpg using gpg to remove the key errors. That seemed to work to fix the update process and I was hoping would fix the following.

All of the files were downloaded on a Win7 machine. Opened in Notepad++ and saved again using a Unix format. The .txt files are the Windows files I didn't clean up.

Also, what is up with the pool? I don't remember seeing that on the repository downloads.

Thank you for all of your assistance. 

```
@-desktop:/repository/dists/lucid$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-worker apache2-utils apache2.2-bin apache2.2-common libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom
The following NEW packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-bin apache2.2-common libapr1 libaprutil1 libaprutil1-dbd-sqlite3
  libaprutil1-ldap
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3,328kB of archives.
After this operation, 10.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err file:/repository/ lucid/main libapr1 1.3.8-1build1
  File not found
Err file:/repository/ lucid/main libaprutil1 1.3.9+dfsg-3build1
  File not found
Err file:/repository/ lucid/main libaprutil1-dbd-sqlite3 1.3.9+dfsg-3build1
  File not found
Err file:/repository/ lucid/main libaprutil1-ldap 1.3.9+dfsg-3build1
  File not found
Err file:/repository/ lucid/main apache2.2-bin 2.2.14-5ubuntu8
  File not found
Err file:/repository/ lucid/main apache2-utils 2.2.14-5ubuntu8
  File not found
Err file:/repository/ lucid/main apache2.2-common 2.2.14-5ubuntu8
  File not found
Err file:/repository/ lucid/main apache2-mpm-worker 2.2.14-5ubuntu8
  File not found
Err file:/repository/ lucid/main apache2 2.2.14-5ubuntu8
  File not found
Failed to fetch file:///repository/pool/main/a/apr/libapr1_1.3.8-1build1_i386.deb  File not found
Failed to fetch file:///repository/pool/main/a/apr-util/libaprutil1_1.3.9+dfsg-3build1_i386.deb  File not found
Failed to fetch file:///repository/pool/main/a/apr-util/libaprutil1-dbd-sqlite3_1.3.9+dfsg-3build1_i386.deb  File not found
Failed to fetch file:///repository/pool/main/a/apr-util/libaprutil1-ldap_1.3.9+dfsg-3build1_i386.deb  File not found
Failed to fetch file:///repository/pool/main/a/apache2/apache2.2-bin_2.2.14-5ubuntu8_i386.deb  File not found
Failed to fetch file:///repository/pool/main/a/apache2/apache2-utils_2.2.14-5ubuntu8_i386.deb  File not found
Failed to fetch file:///repository/pool/main/a/apache2/apache2.2-common_2.2.14-5ubuntu8_i386.deb  File not found
Failed to fetch file:///repository/pool/main/a/apache2/apache2-mpm-worker_2.2.14-5ubuntu8_i386.deb  File not found
Failed to fetch file:///repository/pool/main/a/apache2/apache2_2.2.14-5ubuntu8_i386.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
@-desktop:/repository/dists/lucid$ 
```



```
ls -R /repository
repository/:
dists

repository/dists:
lucid

repository/dists/lucid:
Contents-i386.gz
main
multiverse
public.key
Release
Release.gpg
Release.gpg.bak
Release.gpg.txt
Release.txt
restricted
universe

repository/dists/lucid/main:
binary-i386

repository/dists/lucid/main/binary-i386:
Packages.bz2
Packages.gz
Release
Release.txt

repository/dists/lucid/multiverse:
binary-i386

repository/dists/lucid/multiverse/binary-i386:
Packages.bz2
Packages.gz
Release
Release.txt

repository/dists/lucid/restricted:
binary-i386

repository/dists/lucid/restricted/binary-i386:
Packages.bz2
Packages.gz
Release
Release.txt

repository/dists/lucid/universe:
binary-i386

repository/dists/lucid/universe/binary-i386:
Packages.bz2
Packages.gz
Release
Release.txt
```

---

### Post by Habitual on 2012-06-09
[http://www.bournetoraiseshell.com/article.php/20101207105453509]("http://www.bournetoraiseshell.com/article.php/20101207105453509?query=repository")
[http://www.bournetoraiseshell.com/article.php/20101130132052488]("http://www.bournetoraiseshell.com/article.php/20101130132052488?query=repository")

Sourced from reading these:
[http://wiki.debian.org/HowToSetupADebianRepository](http://wiki.debian.org/HowToSetupADebianRepository) or
[http://www.debian-administration.org/articles/336](http://www.debian-administration.org/articles/336) or
[http://www.debian-administration.org/articles/337](http://www.debian-administration.org/articles/337)

HTH.

---

### Post by adelsin on 2012-06-09
Habitual,

thank you for the response! The sites linked mention quick roll outs of individual packages but don't mention a complete roll out of the entire repository with the packages precluded.

I was trying to follow the examples mentioned in this site: [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

I think it has something to do with the directory structure. I am completely unsure. 

I did try sudo apt-get clean and a apt-get update. Same error when attempting to install the package again. It can't seem to find the files needed.

v/r

---

### Post by Habitual on 2012-07-07
Yes, the link I [provided]("http://www.bournetoraiseshell.com/article.php/20101207105453509") discusses the "offline repo" method of installing.
Mirroring an entire Official Ubuntu repo will require lots of hd space, if that is what you intend, else I can only conclude that you may wish to only mirror select packages?
If that is the case, then apt-get -d (I think is the 'download only' option), still the sources.list would have to be modified in the same manner.

Either way, the mechanism would be the same...
[http://www.bournetoraiseshell.com/article.php/20101207105453509](http://www.bournetoraiseshell.com/article.php/20101207105453509) re:
```

[FONT=monospace]sudo cp /etc/apt/sources.list /etc/apt/sources.list.org
sudo vi /etc/apt/sources.list[/FONT]
```[FONT=monospace]
remove everything and insert 
[/FONT]```
[FONT=monospace]**[COLOR=Red]deb file:[/COLOR]**/path/to/your/repo/dir/ /
sudo apt-get update[/FONT]

```Where the rubber hits the road is```
[FONT=monospace]# Documented by John Jones
# Written up on Tues 07 Dec 2010
# Last Modified on Wed 08 Dec 2010 09:58:19 AM EST
# Reviewed and revised on Thu Dec 09, 2010 @ 10:02:42 AM EST
# user=sypris

sudo apt-get install -y debconf-utils dpkg-dev
mkdir -p Respository/mysql
sudo apt-get clean && sudo apt-get install -y -d mysql-server 
sudo cp /var/cache/apt/archives/ /home/sypris/Repository/mysql && sudo apt-get clean
cd /home/sypris/Repository/mysql && sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
sudo cp /etc/apt/sources.list /etc/apt/sources.list.org
sudo vi /etc/apt/sources.list
remove everything and insert 
deb file:/home/sypris/Repository/mysql/ /
sudo apt-get update
[/FONT]
```
Subscribed with interest...

---

