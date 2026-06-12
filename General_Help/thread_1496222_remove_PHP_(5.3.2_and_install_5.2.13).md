---
title: "remove PHP (5.3.2 and install 5.2.13)"
date: 2010-05-29
forum: General Help
---

### Post by fieldway on 2010-05-29
I installed Ubuntu server 10.4.  during the install i selected to have the LAMP package install.  Now I want to remove PHP (version 5.3.2) and replace it with version 5.2.13, as version 5.3.2 does not work with Moodle (1.9.4) and hoping 5.2.13 will.

How do I remove version 5.3.2

How do I install version 5.2.13


Thanks

---

### Post by kwrjcr on 2010-06-08
I also need to know how to do this, if anyone has any idea how to do this.

---

### Post by ingjoh on 2010-06-09
Looks like the Canonical team has made a big mistake by putting PHP 5.3 and Moodle 1.9.4 together. I realy need to get this fixed!!

---

### Post by ojay on 2010-07-07
I also have the same problem, has anyone been able to figure out how to remove PHP 5.3 and install PHP 5.2... ?

---

### Post by dentalengine on 2010-10-04
Too bad this thread is a few months old. This is exactly what I'm looking for as well. However, my app is Magento, not Moodle. It has the same requirements though, PHP 5.2.13+ but several report is not playing well with 5.3. I was hoping someone would have updated this or given some suggestions of how to get this downgraded.

I have found several links of how to get 5.2.10 but I fear this is too far back for my Magento app to install.

Thank!

---

### Post by EndersJ on 2010-10-21
I've been having these same compatibility problems with Moodle downloaded from the repository and PHP 5.3. I came across some suggestions for downgrading to PHP 5.2.X but haven't been able to confirm or deny their usefulness, just thought I'd share:

[http://ubuntuforums.org/showthread.php?t=1459163](http://ubuntuforums.org/showthread.php?t=1459163)

[http://ubuntuforums.org/archive/index.php/t-1447401.html](http://ubuntuforums.org/archive/index.php/t-1447401.html)

[http://mrkandy.wordpress.com/2010/04/16/install-php-5-2-x-in-ubuntu-10-04-lucid/](http://mrkandy.wordpress.com/2010/04/16/install-php-5-2-x-in-ubuntu-10-04-lucid/)

---

### Post by EndersJ on 2010-10-21
So I was able to solve this problem on my end today using a different method. Rather than downgrade PHP 5.3.X to PHP 5.2.X, which I couldn't confidently accomplish, I upgraded my Moodle version. Currently, the Moodle version in the repository (1.9.4, I think) is incompatible with PHP 5.3. However, you can go to Moodle's  standard package download page ([http://download.moodle.org/](http://download.moodle.org/)) and download the tarball (.tgz) for the latest release (currently, 1.9.9+). I got hung up a little on the next step but eventually figured out that if you extract the folder to /var/www (which to my understanding is the root web directory) you can begin the installation by simply typing "http://localhost/moodle" into a browser address bar.

Just make sure you uninstall the previous moodle version. Going through the Synaptic package manager and right clicking on Moodle and choosing "Select for complete removal" and hitting "Apply" seemed to work just fine.

---

