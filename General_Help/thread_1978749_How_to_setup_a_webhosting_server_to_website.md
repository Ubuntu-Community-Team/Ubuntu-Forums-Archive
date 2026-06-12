---
title: "How to setup a webhosting server to website"
date: 2012-05-12
forum: General Help
---

### Post by Torndown on 2012-05-12
Hi Guys i am new to Ubuntu i'm downloading the 64 bit os as i am speaking i no how to mount the iso but my question is that i want to sell hosting space from home from my website how do set the server up to my website couldn't find anythink in google that can help me i have adsl 2 boardband have 8 TB hards to each harddrive and want to sell some free space as a home business 
Mike

---

### Post by fragos on 2012-05-12
1st install "tasksel" which will help you insure all the parts you need get installed. Open a terminal window and run "sudo tasksel" and you'll be prompted for your user password. Use your down cursor key until the cursor block is on the LAMP server line. The space bar will now toggle an * to select LAMP. Hit the Tab key and cursor moves to <OK>. Now hit return. Apache2, PHP and MYSQL will be installed.

You'll need to enable PHP. To do that, edit /etc/apache2/httpd.conf adding the following 3 lines:

    LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
    AddType application/x-httpd-php .php .phtml
    AddType application/x-httpd-php-source .phps

Open up whatever web browser you use and enter address "localhost" which will display an indication that you were successful. Your web server stores it's sites at /var/www which is owned by root. Open up that folder and you'll see the index.html that tested your install. I use the my web server to debug web sites I create that require PHP so my help stops here. I do know you'll need to tell your firewall not to block calls to your web server. I'd advise you get a static IP address from your ISP to simplify the setup of DNS servers that will be required to point particular domain names to your server.

---

### Post by Torndown on 2012-05-13
thanks for that i shall try that i shall ring dodo for  static IP address cause i want to locate the 192 all what ever the number is if the ip address to a my hosting name so i can up load my owe site 
Mike

---

