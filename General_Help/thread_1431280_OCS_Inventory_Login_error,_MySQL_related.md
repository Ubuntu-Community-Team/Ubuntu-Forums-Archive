---
title: "OCS Inventory Login error, MySQL related"
date: 2010-03-16
forum: General Help
---

### Post by mindwip on 2010-03-16
Hello all,

I have been trying to set up GLPI with OCS inventory but am having issues installing OCS. I have been following the below directions and when i go to [http://localsever/ocsreports](http://localsever/ocsreports) the login page gives me an error.

> Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'ocs'@'localhost' (using password: YES) in /var/www/ocsreports/preferences.php on line 326

ERROR: MySql connection problem
Access denied for user 'ocs'@'localhost' (using password: YES



 Now i have not tried to log in yet so its like there is a auto log in. What config file do i have to edit to turn this off?

Something that may be effecting this would be the following step (below high lighted in red)i do not do as i do not see this line when installing. I am installing 1.3.1 not 1.0 like the guide was written for, which i think is what is causing me not to see this step.

Any help would be great!



 [HOW TO] OCS Inventory
This install procedure was meant for Debian Etch but should work for Ubuntu. Just add sudo to the beginning of all the commands. Or you can login as root and run them by typing:
sudo su

At a command prompt type:

apt-get install apache2 libapache2-mod-php5 php5-cli php5-common php5-cgi mysql-server php5-mysql

apt-get install build-essential

apt-get install libapache2-mod-perl2 php5-gd libxml-simple-perl libcompress-zlib-perl libdbi-perl libdbd-mysql-perl libapache-dbi-perl php-pear php5-dev libnet-ip-perl

/etc/init.d/apache2 restart

cpan SOAP::Lite
select all defaults for cpan installation
select mirrors near you when asked
you will have to press enter and type "yes" when cpan is ready to install SOAP::Lite
use defaults for any questions asked


I also like to install phpmyadmin for easy DB administration.
apt-get install phpmyadmin

You should change your mysql admin password to something other than nothing

wget [http://superb-west.dl.sourceforge.ne...ER_1.01.tar.gz](http://superb-west.dl.sourceforge.ne...ER_1.01.tar.gz)

tar xzvf OCSNG_LINUX_SERVER_1.01.tar.gz

cd OCSNG_LINUX_SERVER_1.01

sh setup.sh

[COLOR="Sienna"]When asked the following question:
Where is Apache root document directory [] ?
Type: /var/www/[/COLOR]

Go to URL [http://IP](http://IP) of server/ocsreports

Enter your root mysql login and password. Use localhost for the MySql HostName

After its done creating the DB, click the "Submit Query" button

You will now be invited to login to your OCS Inventory installation.
Login: admin
Password: admin

Moddified from [http://www.debianadmin.com/automatic...entory-ng.html](http://www.debianadmin.com/automatic...entory-ng.html)


The OCS Inventory site has some decent instructions for deploying the inventory agent.

---

### Post by mindwip on 2010-03-16
never mind, appach2 phpmyadmin was pointing to a invalid file, after deleting the file and reinstalling phpmyadmin and adding account ocs in phpmyadmin the problem was solved.

---

### Post by lonetree on 2010-12-31
Hi Mindwip,

do you mind sharing your experience on setting up an OCS Inventory server with ubuntu? I have been trying to search for a good tutorial but seems that I couldn't get one with step by step guidance.

Thanks

Regards,

lonetree

Happy New Year! 2011

---

