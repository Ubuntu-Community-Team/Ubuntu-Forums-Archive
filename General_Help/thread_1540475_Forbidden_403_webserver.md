---
title: "Forbidden 403 webserver"
date: 2010-07-27
forum: General Help
---

### Post by David-IT on 2010-07-27
Hello i am running ubuntu 10.04 32bit i am currently trying to set up a web-server using apache2 i have installed lamp using
> sudo apt-get install lamp-server^ and also tried un-installing the whole thing and installing php5 mysql-server apache2 separately and still have the same issue my issue is Forbidden-403 but when i first went to localhost in my web-browser it displays the confirmation message  that says it works from apache and that i have nothing in there so it can display what is in www folder but after that aka www/forums it cannot... i am trying to install vbulletin i have tried doing commands like 
> sudo chmod -R 755 /var/www and i have tried i believe every single tutorial google has to offer in the past 4 days of searching :S also this one and still no luck [http://ubuntuforums.org/showpost.php?p=1590980&postcount=2]("http://ubuntuforums.org/showpost.php?p=1590980&postcount=2")i will also post screen of what i mean :D 
Localhost:
[IMG]http://i256.photobucket.com/albums/hh185/dl152567/403/Screenshot-5.png[/IMG]
Then when i try to access my forums:
[IMG]http://i256.photobucket.com/albums/hh185/dl152567/403/Screenshot-1.png[/IMG]

---

### Post by byStanderone on 2010-07-27
...hope there's something here: [http://www.checkupdown.com/status/E403.html](http://www.checkupdown.com/status/E403.html)

---

### Post by David-IT on 2010-07-27
> **byStanderone said:**
> ...hope there's something here: [http://www.checkupdown.com/status/E403.html](http://www.checkupdown.com/status/E403.html)

hey bro thanks for the link greatly appreciated before that link i did not really know what the 403 forbidden message meant but i understand it pretty well know so aka its my end that is the problem the web-page can navigate there but it is probably a permissions issue :( i wonder how in the world i can fix it guess its time for more research

---

### Post by David-IT on 2010-07-28
well guys i might safely assume that i am screwed :( i tried fixing it all night also but still no good :S i am going to keep on it and hopefully fix this problem before monday or i am going to have to go back to crappy windows....

---

### Post by dino99 on 2010-07-28
cant help much on that issue but look closely errors logged

---

### Post by hudsonl on 2010-07-28
You can install everything for LAMP using:
 
sudo tasksel install lamp-server
 
That being said ... you need to put an file (index.html or index.php) in your "cannabis" directory ... **OR** allow directory browsing.
 
To quickly test it ... create an index.html and throw it in that directory.
 
**_Method 1_**
 
1. Create a blank file call "index.html" with something like:
 
<html> 
<b> Cannabis </b>
</html>
 
2. Copy index.html to /var/www/cannabis
 
sudo cp index.html /var/www/cannabis
 
**_Method 2_**

To allow directory browsing .... 
You need an .htaccess file in cannabis directory **or** edit your sites-enabled conf file
 
Create an .htaccess file in /var/www/cannabis ... with the following line
 
Options indexes
 
 
**OR**
 
edit your sites-enabled config file and add the following:
 
<Directory /var/www/cannabis>
Options Indexes 
</Directory>
 
 
Probably named something like "/etc/apache2/sites-enabled/000-default"
 
 
Good Luck

---

### Post by David-IT on 2010-07-28
> **hudsonl said:**
> You can install everything for LAMP using:
 
sudo tasksel install lamp-server
 
That being said ... you need to put an file (index.html or index.php) in your "cannabis" directory ... **OR** allow directory browsing.
 
To quickly test it ... create an index.html and throw it in that directory.
 
**_Method 1_**
 
1. Create a blank file call "index.html" with something like:
 
<html> 
<b> Cannabis </b>
</html>
 
2. Copy index.html to /var/www/cannabis
 
sudo cp index.html /var/www/cannabis
 
**_Method 2_**

To allow directory browsing .... 
You need an .htaccess file in cannabis directory **or** edit your sites-enabled conf file
 
Create an .htaccess file in /var/www/cannabis ... with the following line
 
Options indexes
 
 
**OR**
 
edit your sites-enabled config file and add the following:
 
<Directory /var/www/cannabis>
Options Indexes 
</Directory>
 
 
Probably named something like "/etc/apache2/sites-enabled/000-default"
 
 
Good Luck

hey brother i deleted everything and reinstalled it all with the command you gave me it actually ran through set up and installed perfectly i cannot thank you enough :DDDDD but i did have to change the permissions to the folders after i reinstalled it made them all root lol but that was easy just did 
> 
sudo chmod david /var/www/since alt+f2 
> sudo nautilus did not work ha-ha :D thank you so much if you want to check out my forums(they are not even ready yet lol) check them out at(for some reason godady does not let me redirect my domain to my ip but i am pretty sure it is a easy fix emailed them already) [http://68.123.250.23/]("http://68.123.250.23/")and it goes directly to index i will probably fix that when i find out how ha-ha i am just so ex-static i do not have to go back to windows thank you man you don't understand how happy this made me :DD

---

### Post by hudsonl on 2010-07-28
Glad to hear that it worked for you !!

The site looks great ... if you want to change document root ... edit the config file in sites-enabled and change 

**From:**        DocumentRoot /var/www
 


**To:**        DocumentRoot /var/www/forums


 Again ... probably **/etc/apache2/sites-enabled/000-default**

Restart Apache by running the following:

sudo /etc/init.d/apache2 restart


By the way ...  gksudo nautilus will open nautilus with root priv


The other way to open up to forums automatically (if you don't want to change the document root) is create an index.php file that re-directs to the forums subfolder.
But personally ... the best way is change document root ... if that will be the main page.

Also, GoDaddy should allow DNS redirect where you create a sub-domain like:

forums.mysite.com  and in their DNS tools put your IP address there.


Take Care  :)

---

