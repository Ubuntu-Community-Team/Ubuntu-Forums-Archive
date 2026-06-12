---
title: "Lemon Point of sale"
date: 2010-12-10
forum: General Help
---

### Post by al-qarni on 2010-12-10
Hi there people. I am very new to linux. I wish to migrate, but things look very confusing, and i'm still not sure what to do. 
I want to install lemon POS 
[http://lemonpos.org/](http://lemonpos.org/)
but i find it very difficult to install this on my PC. Here is the guide
[http://sourceforge.net/apps/mediawiki/lemonpos/index.php?title=Installation_Guide](http://sourceforge.net/apps/mediawiki/lemonpos/index.php?title=Installation_Guide)
I cant even do the** first** step. Maybe the Author didnt expect newbies like me to use this system. 
I just want this LEMON POS up and running with MYSQL. Can somone guide me. Perhaps remote control my PC?

Thanks

I did however use XUBUNTU SOFTWARE CENTRE, to install LEMON, but i cant get past the MYSQL confuguration bit. it says connection **failed** blah blah blah. This method was **not** instructed by Author

---

### Post by al-qarni on 2010-12-13
Oh, no one here to help. NVM. I did however successfully install LEMON POS and is fully functional. However I want to change my region. Thats why lemon is calculating in Dollars. I want to it to calculate in pounds. So how do i change my region. 

Thanks

---

### Post by faultymem on 2011-06-29
> **al-qarni said:**
> Hi there people. I am very new to linux. I wish to migrate, but things look very confusing, and i'm still not sure what to do. 
I want to install lemon POS 
[http://lemonpos.org/](http://lemonpos.org/)
but i find it very difficult to install this on my PC. Here is the guide
[http://sourceforge.net/apps/mediawiki/lemonpos/index.php?title=Installation_Guide](http://sourceforge.net/apps/mediawiki/lemonpos/index.php?title=Installation_Guide)
I cant even do the** first** step. Maybe the Author didnt expect newbies like me to use this system. 
I just want this LEMON POS up and running with MYSQL. Can somone guide me. Perhaps remote control my PC?

Thanks

I did however use XUBUNTU SOFTWARE CENTRE, to install LEMON, but i cant get past the MYSQL confuguration bit. it says connection **failed** blah blah blah. This method was **not** instructed by Author


Hi

For Ubuntu 10.04LTS 32bit

1)Download the .deb package from this link.
[http://sourceforge.net/projects/lemonpos/files/real/lemonpos_0.9.3-1_i386_ubuntu.10.04.deb/download](http://sourceforge.net/projects/lemonpos/files/real/lemonpos_0.9.3-1_i386_ubuntu.10.04.deb/download)

2)Install MySQL (I install version 5.1)
sudo apt-get install mysql-server-5.1

3)Run the .deb file you downloaded in step 1. You'll be prompted that there is a later version on the software in the software center, just ignore the request to install the newer version and continue to install the lemonpos_0.9.3-1_i386_ubuntu.10.04.deb version.

4)Once installed, run  the following from the terminal.


[LIST]
[*]cd /usr/share/kde4/apps/lemon
[*]cat lemon_mysql.sql | mysql -u root -p (You'll be prompted for the root password for MySQL you defined in step 2 when you installed MySQL.
[/LIST]
5) Install MySQL Administrator from the Software Centre, it help to bulk change items. I played around with it and it's easy enough to understand.


I'm using LemonPOS in my shop and it is perfectly suited for retail. Barcode Scanner worked out the box. The receipt printer was a challenge, I bought a used Epson and with a lot of tweaking got it working.

---

