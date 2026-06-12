---
title: "Installing 10.04 with PHP5.2"
date: 2010-07-09
forum: General Help
---

### Post by pundip on 2010-07-09
I just upgraded and existing install to 10.04 only to discover that php 5.32 does not work with a lot of stuff. I tried to revert back to 5.2 and destroyed everything. I think i have managed to get 5.3 back but apache will not phrase .php anymore. Anyway I want to do a fresh install of 10.4 but install php5.2 when I put back the lamp stack on it. I was wondering what the correct process of doing that may be. If anyone can tell me how to get apache to phrase php again that would be nice as well but i think terms of effort required to fix it would be simpler to follow a standard procedure that should work on a clean install.

---

### Post by quimkaos on 2010-07-09
Backup your server data, uninstall Apache and PHP, then reinstall Apache.
Go to php.net and do a manual install of PHP 5.2 (i don't see PHP 5.2 in the ubuntu repository anymore). you also have instructions on how to do a manual install of PHP on php.net.

and by the way, what doesn't work in 5.3? i didn't noticed anything.

---

### Post by pundip on 2010-07-09
quimkaos thanks for your reply. I was having issues with Atmail and i heard drupal is not working with 5.3 yet. I am not sure but if i remember torrentflux was having an issue for me. Gallery2 was having an issue but as I understand it the new version works.Can you advise what is the best way to purge apache and php from system? There is an apt-get command which does a full uninstall. would it be sudo apt-get purge apache2 php5 ?
Thanks again for replying

---

### Post by quimkaos on 2010-07-09
exactly... apt-get purge apache2 php5, since apt-get remove will leave configuration files. do man apt-get and you'll have a good description of every option. If apt-get purge php5 doesn't work (probably you have the package php5-mysql) try pressing 2 times the tab key after typing apt-get purge, and you'll have a list of the installed packages. If you are using Ubuntu Desktop you could also use the package manager synaptic, but apt-get will be probably faster.

And don't panic just yet! yes, this release of PHP have some backward incompatibilities (posted [here]("http://pt2.php.net/manual/en/migration53.incompatible.php") ) but probably those scripts/applications will be updated to work with 5.3.2.
[IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG]

---

