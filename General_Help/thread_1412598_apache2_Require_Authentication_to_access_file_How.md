---
title: "apache2 Require Authentication to access file: How?"
date: 2010-02-21
forum: General Help
---

### Post by bhencetotozo on 2010-02-21
Hello there guys.
Thank you for taking your time to help me.

I had no problem doing this on Red Hat, but on ubuntu the directories where the files exist are a bit funny, I was not able to make it Required for users to Authenticate in order to access files.

I followed the link below with out success:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialApacheAddingLoginSiteProtection.html]("http://www.yolinux.com/TUTORIALS/LinuxTutorialApacheAddingLoginSiteProtection.html")

I created files .htpasswd  and .htaccess etc. .htgroup,
I also used program htpasswd on terminal to create files, the files wouldn't create. I manually created them.

Anybody has a working guide for ubuntu 9.10? thank you.


Thank you very much for reading this guys. Im about to go back to my ugly redhat again before I cause any phisical damage to my belongins since I have anger problems. :'(

Once again, 
Thank you very much for reading this guys.
I hope I can get help.


-------EDIT-------
Reason for editing:
SOLVED:
------------------

Action taken:
1)
sudo gedit /etc/apache2/httpd.conf

<Directory /var/www/membersonly>
     AllowOverride AuthConfig
     AuthName "Please enter your credentials"
     AuthType Basic
     AuthUserFile /home/dekaronultra.info/membersonly/.htpasswd
     AuthGroupFile /dev/null
     require user xetal_x22TfdD
     </Directory>

2)cd /home/dekaronultra.info/membersonly/
3)sudo htpasswd -c .htpasswd xetal_x22TfdD
4)enter new password, retype new password (it will prompt you)

5)Save file: Restart Apache2, done. ^^ !!! Im happy now, glad I didnt cause any damage to any objects, I was about to loose my patience hahahah !.

Thank you anyways guys... I hope this will help some one.

---

