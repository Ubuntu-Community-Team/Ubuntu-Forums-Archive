---
title: "suphp"
date: 2010-06-01
forum: General Help
---

### Post by Daveran27703 on 2010-06-01
Hello, I am running Ubuntu Server ver 10 and I was trying to get suphp working
 
I was following the instructions on this page [http://www.rickogden.com/2010/01/suphp-userdir-on-ubuntu/](http://www.rickogden.com/2010/01/suphp-userdir-on-ubuntu/)
 
everything went south when I did the last steps
 
sudo a2dismod php5
sudo a2enmod userdir suphp
sudo /etc/init.d/apache2 restart
 
now the web server is broken as I get an Internal Server Error
 
It would be nice if suphp was working, but I would almost be happy if I was just back to where I was.
Can someone guide me on what to do, so as to not have to wipe the drive clean and start totally over :confused:
 
 
 
ok  upon thinking about what I did, I did the following
 
sudo a2dismod userdir suphp
sudo a2enmod php5
sudo /etc/init.d/apache2 restart
 
 
and it is back up and working...  and suggestions on a correct process to get suphp working??

---

