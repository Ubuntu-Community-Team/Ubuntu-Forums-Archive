---
title: "Broken Lamp stack, can't reinstall PHP - HELP"
date: 2009-07-24
forum: General Help
---

### Post by craig100 on 2009-07-24
Hi,

At wits end, need some advice please...

Having just finished quite a large web development, I was adding some more virtual directories to my Apache2 server on Ubuntu 9.04. All of a sudden the virtual servers began to act strangely in that no matter what URL I entered they all went to the same site. I was using WebMin to do this.  

Eventually I decided to deinstall and reinstall Apache. Had to do this a couple of times as I didn't realise the config files stayed on. So having also deinstalled and reinstalled PHP5 and webmin if I go to any url on the server and ask for a PHP file the browser asks if I want to download a phtml file.  I understand that this means PHP5 isn't installed properly but I can't work out how to clean the system out and do a clean re-install of the LAMP stack. Any help would be greatly appreciated.

Craig

---

### Post by credobyte on 2009-07-24
Remove:
```
sudo apt-get remove --purge apache2 php5 libapache2-mod-php5 && sudo rm -r /etc/apache2

```

Install & restart:
```
sudo apt-get install apache2 php5 libapache2-mod-php5 && sudo /etc/init.d/apache2 restart
```

---

### Post by wojox on 2009-07-24
You may also have to :

```
sudo a2enmod php5
```

Then:

```
sudo /etc/init.d/apache2 restart
```

Be sure to clear your browser's cache before testing your site again.

---

### Post by LepeKaname on 2009-07-24
> All of a sudden the virtual servers began to act strangely in that no matter what URL I entered they all went to the same site. 

Check this thread: [http://ubuntuforums.org/showthread.php?t=1198547](http://ubuntuforums.org/showthread.php?t=1198547)


> I go to any url on the server and ask for a PHP file the browser asks if I want to download a phtml file.


Check this thread: [http://www.backports.ubuntuforums.org/showthread.php?t=1175896](http://www.backports.ubuntuforums.org/showthread.php?t=1175896)

I hope this help you.

---

### Post by craig100 on 2009-07-25
Thanks for all your help.  Managed to get back to a clean LAMP install. Now back to adding virtual servers using webmin and finding that if I add more than two then all urls end up at the same site:(  The hosts file is correct so I guess I'll have to look around the net further.

Cheers,

Craig

---

### Post by LepeKaname on 2009-07-25
Did you checked the link I post it?

---

