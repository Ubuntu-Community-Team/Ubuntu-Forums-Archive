---
title: "ubufox cant update, ends with an error"
date: 2011-07-16
forum: General Help
---

### Post by sdowney717 on 2011-07-16
so what can be done to fix this?

> riarron@friarron-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  openssh-client ssh-askpass-gnome ubufox
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 849kB/907kB of archives.
After this operation, 319kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main openssh-client 1:5.3p1-3ubuntu7 [762kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main ssh-askpass-gnome 1:5.3p1-3ubuntu7 [87.1kB]
Fetched 849kB in 1s (459kB/s)           
(Reading database ... 327851 files and directories currently installed.)
Preparing to replace openssh-client 1:5.3p1-3ubuntu6 (using .../openssh-client_1%3a5.3p1-3ubuntu7_i386.deb) ...
Unpacking replacement openssh-client ...
Preparing to replace ssh-askpass-gnome 1:5.3p1-3ubuntu6 (using .../ssh-askpass-gnome_1%3a5.3p1-3ubuntu7_i386.deb) ...
Unpacking replacement ssh-askpass-gnome ...
Preparing to replace ubufox 0.9-0ubuntu1~mfs~lucid1 (using .../ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb) ...
Unpacking replacement ubufox ...
dpkg: error processing /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb (--unpack):
 trying to overwrite '/etc/xul-ext/ubufox.js', which is also in package xul-ext-ubufox 0:0.9-0ubuntu1~mfs~lucid1
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sdowney717 on 2011-07-16
I deleted ubufox package and now no error.
Dont see where ubufox will be missed.

[http://ubuntuforums.org/showthread.php?t=1798062&highlight=ubufox](http://ubuntuforums.org/showthread.php?t=1798062&highlight=ubufox)

this person had same issue as my inlaw's pc.
you can use chrome to translate to english.

---

### Post by sdowney717 on 2011-07-16
found out more info so it is solved for me.
[http://ubuntu4beginners.blogspot.com/2011/06/firefox-5-stable-arrives-in-official.html](http://ubuntu4beginners.blogspot.com/2011/06/firefox-5-stable-arrives-in-official.html)

> We recently talked about Mozilla following a new release cycle for Firefox and Thunderbird. So following that schedule, Firefox 5 stable was released a few days ago just a couple of weeks after Firefox 4 was released after a development cycle that lasted longer than a year.

This time you don't need to add any custom PPA to the Ubuntu releases that come with Firefox 4 by default e.g, Natty Narwhal. Firefox 5.0 is in the official repositories now and you just need to fire-up your Update Manager or run these commands:

sudo apt-get update
sudo apt-get upgrade

So, what did Mozilla achieve in Firefox 5 in just a couple of weeks after the release of Firefox 4? This is what they say:

The latest version of Firefox includes more than 1,000 improvements and performance enhancements.

UPDATE 6/23/2011: The same is also true now for the "firefox-stable" PPA. So, if you installed Firefox 4 in Lucid or Maverick by using this PPA, you, as well, just need to upgrade by following the above stated commands.

In order to do a full successful upgrade, you need to remove the package "xul-ext-ubufox" before, since the package "ubufox" seems to fully replace it now, and won't upgrade then because of the resulting conflict.

sudo apt-get purge xul-ext-ubufox

---

