---
title: "php issue"
date: 2011-03-20
forum: General Help
---

### Post by CNM on 2011-03-20
Hi ,

i am implementing opennac on an ubuntu VM
i have php5 installed
[http://localhost/](http://localhost/) works
when i go to [http://localhost/nac/index.php](http://localhost/nac/index.php) , a blank page shows ...
any ideas ?

i need to solve this ASAP ...

thanks

---

### Post by WorMzy on 2011-03-20
Temporarily turn on error reporting.

```
gksu gedit /etc/php5/apache2/php.ini
```

Find the "display_errors = Off" line (line number 531 on my Lucid install), and change it to "display_errors = On". Then save the file and restart apache

```
sudo /etc/init.d/apache2 restart
```

Then try the page again, and see if there's any errors.

---

### Post by CNM on 2011-03-20
> **WorMzy said:**
> Temporarily turn on error reporting.

```
gksu gedit /etc/php5/apache2/php.ini
```Find the "display_errors = Off" line (line number 531 on my Lucid install), and change it to "display_errors = On". Then save the file and restart apache

```
sudo /etc/init.d/apache2 restart
```Then try the page again, and see if there's any errors.

Thank you for the quick reply :)
i got this error : 
[COLOR=Red]Fatal error: Class 'Logger' not found in /opt/nac/bin/funcs.inc.php on line 51 [/COLOR]

i went to this file and on line 51 i have :
$logger=Logger::getInstance();

---

### Post by WorMzy on 2011-03-20
I've never used opennac before, so I can't really advise you any further. Make sure you've downloaded the full package, and have installed it correctly, then make sure you have all the dependencies. Check the developer's website and see if they have a list of packages you need to install. Also see if they've got a help forum or something where you're more likely to find a solution.

Good luck.

Oh, and remember to turn off error reporting after you've fixed the problem. :)

---

### Post by CNM on 2011-03-20
> **WorMzy said:**
> I've never used opennac before, so I can't really advise you any further. Make sure you've downloaded the full package, and have installed it correctly, then make sure you have all the dependencies. Check the developer's website and see if they have a list of packages you need to install. Also see if they've got a help forum or something where you're more likely to find a solution.

Good luck.

Oh, and remember to turn off error reporting after you've fixed the problem. :)

will do that thanks ...
still need help if anybody has any idea ...

---

