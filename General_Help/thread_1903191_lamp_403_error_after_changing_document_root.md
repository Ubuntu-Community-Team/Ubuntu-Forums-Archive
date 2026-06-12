---
title: "lamp 403 error after changing document root"
date: 2012-01-01
forum: General Help
---

### Post by tech7 on 2012-01-01
Hi everybody.  I've got lamp installed on my Ubuntu-based machine.  Originally, /var/www was my document root folder, as default.  However, I wanted to be able to use ubuntu one to sync my lamp server's document root folder between several computers.  So, like an idiot, I first try to do this on my main development machine (lessons learned, lol).

What I have done, is I had created a folder name www in my /home/user/Documents folder.  Then, changed my /etc/apache2/sites-available/default file to reflect that.  I got error'd.

So, I cp'd this file to /etc/apache2/sites-available/mysite and ran ```
sudo a2dissite default && sudo a2ensite mysite
``` in terminal.

I'm still getting 403'd.

I've restarted apache2 several times and chmod'd the folder to 775.  Still can't get no satisfaction.
Can anybody help?

---

### Post by galvatron408 on 2012-01-02
You must have messed up your configuration.

The fastest way to get this fixed is to revert your changes. Afterwards, just create a soft link from your /home/user/www -> /var/www

just make sure your permission on the dir is somewhere along the line of 770 and your user is in the correct group. (don't make any file 7 permission unless it requires it).

Good Luck

---

### Post by tech7 on 2012-01-09
Got it!  Thanks a lot buddy!

---

