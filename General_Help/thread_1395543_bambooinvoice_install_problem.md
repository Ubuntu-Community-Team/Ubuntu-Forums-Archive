---
title: "bambooinvoice install problem"
date: 2010-02-01
forum: General Help
---

### Post by 19bab79 on 2010-02-01
i am trying to install bamboo invoice and am racking my brain over this problem. whenever i try to get to the page to install i get this in my browser with a blank screen:
[http://192.168.2.5/bambooinvoice/index.php/install/not_installed](http://192.168.2.5/bambooinvoice/index.php/install/not_installed)

i have searched google and the bambooinvoice forum, but nothing seems to work. i started out using this guide:
[http://www.bambooinvoice.org/bamboo_install_guide.pdf](http://www.bambooinvoice.org/bamboo_install_guide.pdf)

i am running ubuntu server, apache2, mysql, and php5. my base url in the config.php is [http://192.168.2.5/bambooinvoice/](http://192.168.2.5/bambooinvoice/)
i have put all of the files that were in the zip file into the directory /var/www/bambooinvoice after unpacking.

can someone please help me?

---

### Post by DeMus on 2010-02-01
The links starting with 192.168 won't work on the net since they point to internal addresses on your own network.
You have to attach the page to your post for others to see it.

---

### Post by 19bab79 on 2010-02-01
i was just giving an example of what the url looks like after i input 192.168.2.5/bambooinvoice/ and hit enter. i don't have a static ip to let people navigate to it. all it is, is the url posted above and a white screen. it also acts like it is still trying to connect to the site but never connects.

---

### Post by t4thfavor on 2010-02-01
Did you go through all steps carefully, and watch for errors?

Create Database?
Correct credentials in the database config?

howabout  [http://www.yoursite.com/index.php/install](http://www.yoursite.com/index.php/install) .

you may have to complete the last step (removing the install files, just move em) before it will work. If you can, try rebootint to see if anything gets started.


If it has any technical information, it would really help to see a screen shot.

---

### Post by 19bab79 on 2010-02-01
i have followed the instructions, but i don't even get a chance to enter credentials. i enter the 192.168.2.5/bambooinvoice into the address bar and hit enter and this pops up in the address bar:
[http://192.168.2.5/bambooinvoice/index.php/install/not_installed](http://192.168.2.5/bambooinvoice/index.php/install/not_installed)

it also constantly says "loading..." on the tab and "waiting for 192.168.2.5..." at the bottom of the page. the whole page is blank. I have checked /var/log/apache2/access.log and can see that i am accessing the machine. /var/log/apache2/error.log shows no errors.

i put a php info script into the /var/www/bambooinvoice directory and it shows the php info just fine. not sure what i am doing wrong.

---

### Post by 19bab79 on 2010-02-01
man, i got it. first i had not added email, password, contact into the install.php. the reason i was getting the white screen was because i needed to change the uri protocol in the config.php. i changed it to REQUEST_URI and it worked perfectly.

---

