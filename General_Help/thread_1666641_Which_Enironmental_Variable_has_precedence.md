---
title: "Which Enironmental Variable has precedence?"
date: 2011-01-14
forum: General Help
---

### Post by micha8l on 2011-01-14
Hello,

I have php installed on my system, but recently I installed Zend Framework CE which comes with php 5.3, Pear, Pdo and a load of other good stuff. However whenever I invoke php or pear in BASH it doesn't load up Zend's php, it loads up the php I had on my system prior to Zend's instillation.

Steps I've taken so far was to edit my /etc/bash.bashrc file with the following:

> 
PATH=$PATH:/usr/local/zend/bin
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/zend/lib
alias zf="zf.sh"
The directory /usr/local/zend/bin contains my PHP binaries and config files.

Next I changed directory to /usr/bin and located and deleted php-config, phpize, pear, peardev, and pecl. I symlinked in replacement files -- with same names, but configured for Zend Server -- from /usr/local/zend/bin. At this point I could invoke php and pear for Zend Server from the shell, everything is working fine, for now....

Update manager informed me of a PHP update, so being the amateur I am thinking nothing of it, I hit update. Disaster! When I go to the shell and type php, pear it once again invokes my old php and pear. I checked my /usr/bin/ directory and the files I deleted are back and have overridden (no deleted) my symlinks from /usr/local/zend/bin!

All of the above took me two days to accomplish, reading wiki, searching Google, posting here. All I wanted was to have a working development environment and I end up learning about the inner workings of the shell *sigh.* and worse part is I don't think I'm doing things right :D So ultimately my question is: where can I stick files I symlinked above so that they take precedence over the ones in /usr/bin? 


Kind Regards,
Mike :P

---

### Post by anglican on 2011-01-14
> **micha8l said:**
> Hello,

I have php installed on my system, but recently I installed Zend Framework CE which comes with php 5.3, Pear, Pdo and a load of other good stuff. However whenever I invoke php or pear in BASH it doesn't load up Zend's php, it loads up the php I had on my system prior to Zend's instillation.

Steps I've taken so far was to edit my /etc/bash.bashrc file with the following:

The directory /usr/local/zend/bin contains my PHP binaries and config files.

Next I changed directory to /usr/bin and located and deleted php-config, phpize, pear, peardev, and pecl. I symlinked in replacement files -- with same names, but configured for Zend Server -- from /usr/local/zend/bin. At this point I could invoke php and pear for Zend Server from the shell, everything is working fine, for now....
I wouldn't do it this way - for the reason you've just discovered. Simply change the /etc/bash.bashrc entries to:
> PATH=/usr/local/zend/bin:$PATH
LD_LIBRARY_PATH=/usr/local/zend/lib:$LD_LIBRARY_PATHand leave everything in /usr/bin as it is. Oh, and I wouldn't change /etc/bash.bashrc either, but rather ~/.bashrc.

H

---

