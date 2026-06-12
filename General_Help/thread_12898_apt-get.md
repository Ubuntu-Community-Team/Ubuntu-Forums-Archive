---
title: "apt-get"
date: 2005-01-27
forum: General Help
---

### Post by gogodidi on 2005-01-27
just wondering how this really works, how powerful the comamnd is

can you write anything after the install?

so would

apt-get install kde3.3.2 work (i'm going to be new to debian, going to install it at home tomorrow))

because I prefer kde to gnome, but I prefer ubuntu to mepis. 

could I say

apt-get install smb4k

?

because I like that program..  lots

---

### Post by Rule on 2005-01-27
just apt-get install kde and it will install the latest version, you can also use synaptic which is the gui frontend for apt.

---

### Post by az on 2005-01-27
Apt is great, but it is not magic.

You have a list of software repositories.  On this list, by default are all the packages on the cd.  You may add repositories.  These repositories are on the net.  When you add a repository, you add to your database of packages.

You need to update the database with

apt-get update
or else it will not notice that you have added repositories.

apt-cache search editor

that will give you a list of any package that has the word editor in it's description or name.

apt-cache show abiword

That will show you the detailed information about that package.

apt-get install abiword

That will install all the packages you need to run abiword.  If it depends on libraries, it will list them out and ask you if it is okay to continuewiththe installation.  It will then download the packages fromthe net and install and configure them for you.

If a package you want to install or need to install to meet a dependancy conflicts with another package, you will be prompted to see if youreally want to remove the other packages first.  If the packages are too important and will render your system unusable, it will complain and not go ahead.

You do not need to runthese commands, you can just use synaptic.  It does aol the work for you.

So, if you want kde, fireup synaptic and search the database of available packages for kde.  If you cannot find it, youneed to enable a repository where you can find it (try universe).  Update you database and try again.  Mark it for installation and tell it to go ahead...

---

