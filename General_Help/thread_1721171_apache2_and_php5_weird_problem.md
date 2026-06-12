---
title: "apache2 and php5 weird problem"
date: 2011-04-04
forum: General Help
---

### Post by cyclobs on 2011-04-04
okay just installed php5 and apache2 to run a website i'm working on atm for work. php is installed in apache and works fine by doing a phpinfo()

but when i load up my website none of my php code is working. the site still comes up but pretty much everything to do with php is gone (which is basically the whole site apart from a couple of formatting things)

any ideas?

---

### Post by domu on 2011-04-04
Think we probably need a bit more info to help you. What pages are your loading for your website? Do they end with php suffix or something different? In general pages called 'htm', 'html' etc are not pre-processed for php, though you can alter this behaviour by editing a line in your /etc/apache2/mods-enabled/php5.conf:

<FilesMatch "\.ph(p3?|tml)$">

alter to:

<FilesMatch "\.p?h(p3?|tml?)$">

and then restart apache:

sudo /etc/init.d/apache2 restart

---

### Post by cyclobs on 2011-04-04
i've found the issue. for some reason by default the php error output was disabled. so the php was actually working on my server but i couldn't see that it was returning errors.

i made the site on my windows portable apache2 php5 server and just copied and pasted over the files onto my linux server so i can work here but for some reason it's not access local files by include ('folder/file.php')

is this a php setting somewhere or am i forgetting something about developing sites on linux?

---

### Post by dazman19 on 2011-04-04
by default if you used the package manager to install apache2 and php5 your web folder is /var/www

Then you need to make sure that the owner is www-data

sudo chown www-data:www-data /var/www

if you have gone chmod (some number) (your username) /var/www 
you might have taken acess away from the www-data user.

---

### Post by gpdas on 2011-04-04
what comes in your browser when you type [http://localhost](http://localhost) in the address bar?

---

### Post by cyclobs on 2011-04-04
i found the issue.

main include folder was 'Include' which works on windows but not on linux :| should of been 'include'

---

