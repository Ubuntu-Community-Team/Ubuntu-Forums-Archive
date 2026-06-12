---
title: "Unable to install Drupal6 on Ubuntu 8.04"
date: 2009-07-19
forum: General Help
---

### Post by EricT_206 on 2009-07-19
I am new to Linux and Ubuntu and have very limited knowledge. That said...
 
Am trying to install Drupal6 on Ubuntu Server 8.04. I enter:
sudo apt-get install drupal6
 
Result is:
E: couldn't find package drupal6
 
I already uncommented all the URLs in /etc/apt/sources.list and ran sudo apt-get update. What else should I try?
 
Thanks,
Eric

---

### Post by utnubuuser on 2009-07-19
worked ok when I tried a dry-run.  I've found drupal installs easier to work with when you get the source (tar.gz) files from drupal, download, and extract to /var/www.

---

