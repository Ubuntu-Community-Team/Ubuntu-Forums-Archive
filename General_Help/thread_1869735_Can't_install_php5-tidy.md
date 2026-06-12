---
title: "Can't install php5-tidy"
date: 2011-10-26
forum: General Help
---

### Post by GeordieTroutman on 2011-10-26
I'm trying to install php5-tidy using the following command:

sudo apt-get install php5-tidy

However, this fails and displays the following message:

The following packages have unmet dependencies:
  php5-tidy: Depends: php5-common (= 5.2.4-2ubuntu5.18) but 5.2.8-0.dotdeb.1 is to be installed
E: Broken packages

The server is in use hence I'm very wary of breaking things. I'm not sure how to proceed to get around this?

---

### Post by GeordieTroutman on 2011-10-26
Ok, got this working.

Followed the instructions in this post - [http://ubuntuforums.org/showthread.php?t=195636](http://ubuntuforums.org/showthread.php?t=195636)

Had to grab source code for php-5.2.17 from php site. 
 
 when I ran ./configure had to get the following before it compiled.
 
 apt-get install libtidy-dev
 apt-get install re2c
 
 /etc/init.d/apache2 restart

Sorted!

---

