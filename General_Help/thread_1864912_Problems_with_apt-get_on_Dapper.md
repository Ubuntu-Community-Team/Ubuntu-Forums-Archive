---
title: "Problems with apt-get on Dapper"
date: 2011-10-19
forum: General Help
---

### Post by Gazdaman on 2011-10-19
Hi guys,

Firsty bear with me, I'm not amazing with Linux, once it's set up I just tend to let it run!

Until today when I needed to update to php5.

When I use apt-get I get lots of errors about logins being incorrect, and/or files not being found. I assumed it was a sources.list problem, so I added a few more servers but still to the same end.

```

root@lvps94-136-59-106:/home/gaz/# apt-get install php5 libapache2-mod-php5
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  php-pear
The following packages will be REMOVED:
  libapache2-mod-php4 psa-php4-configurator
The following NEW packages will be installed:
  libapache2-mod-php5 php5
0 upgraded, 2 newly installed, 2 to remove and 8 not upgraded.
Need to get 2262kB of archives.
After unpacking 1970kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libapache2-mod-php5 php5
Install these packages without verification [y/N]? y
Get:1 ftp://80.237.136.138 dapper-security/main libapache2-mod-php5 5.1.2-1ubuntu3.9 [2261kB]
Err ftp://80.237.136.138 dapper-security/main libapache2-mod-php5 5.1.2-1ubuntu3.9
  Unable to fetch file, server said 'Failed to open file.  '
Get:2 ftp://80.237.136.138 dapper-security/main php5 5.1.2-1ubuntu3.9 [1044B]
Get:3 ftp://archive.ubuntu.com dapper-security/main libapache2-mod-php5 5.1.2-1ubuntu3.9 [2261kB]
Err ftp://archive.ubuntu.com dapper-security/main libapache2-mod-php5 5.1.2-1ubuntu3.9
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 91.189.92.181 21]
Get:4 ftp://archive.ubuntu.com dapper-security/main php5 5.1.2-1ubuntu3.9 [1044B]
Err ftp://archive.ubuntu.com dapper-security/main php5 5.1.2-1ubuntu3.9
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 91.189.92.181 21]
Failed to fetch ftp://archive.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.1.2-1ubuntu3.9_i386.deb  Unable to fetch file, server said 'Failed to open file.  ' [IP: 91.189.92.181 21]
Failed to fetch ftp://archive.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.1.2-1ubuntu3.9_all.deb  Unable to fetch file, server said 'Failed to open file.  ' [IP: 91.189.92.181 21]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@lvps94-136-59-106:/home/gaz/#

```

So that's where I stand, unable to update PHP. When I delved a bit further it turns out I'm still running dapper, and surely it's time I updated the dist.

But I can't do that, because I can't apt-get install update-manager-core.

So any input on where my actual problem lies would be greatly received. If there's no benefit from updating from Dapper, then I won't. I only want/wanted to because I can't help but think it's linked to the problems I'm having (and it's about time).

I've done an apt-get update, and apt-get upgrade. Both fail with similar errors as above.

Thanks,

Gaz

---

### Post by snowpine on 2011-10-19
Dapper Drake is "end of life" so upgrading requires a couple of extra steps:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You might have better results simply backing up your data and doing a fresh install of the current 10.04 Long-Term Support release from: [http://ubuntu.com](http://ubuntu.com)

---

### Post by TeoBigusGeekus on 2011-10-19
Dapper is no longer supported, therefore its repositories are dead,
Install a newer version.

---

### Post by dniMretsaM on 2011-10-19
Your best would be to back up all your data and do a fresh install of the current LTS server (10.04 Lucid Lynx) which can be found [here](http://www.ubuntu.com/download/server/download).

---

### Post by Gazdaman on 2011-10-19
I thought that might be the case. I would do a fresh install, but this is a server in a datacentre in god-knows-where. So whatever I want to do, it needs doing over SSH, hence upgrading.

I'll see how I get on with the EOLUpgrades link. Thanks for now!

Gaz

---

### Post by Gazdaman on 2011-10-19
Hmm, 

It's not gone well, when I add the repositories as listed in the EOL link I can apt-get the update-core-manager, and I can successfully apt-get update and upgrade. All of which worked fine.

But when I do-release-upgrade I get load of failed errors, a few files downloaded, but it ends in:

```
Getting upgrade prerequisites failed

The system was unable to get the prerequisites for the upgrade. The
upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and
include the files in /var/log/dist-upgrade/ in the bugreport.


Restoring original system state

Aborting
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
root@lvps94-136-59-106:/etc/apt#

```.

So that's gone **** up, so to speak. My next option is to try and get in contact with the datacentre place and see if they'll do me a fresh install of an updated LTS.

Gaz

---

