---
title: "website to preview localhost files"
date: 2009-08-26
forum: General Help
---

### Post by calvinlyp on 2009-08-26
Hi all,

i am new to ubuntu.
Currently i am using 8.04 and 8.10 version of ubuntu.
i am trying to create a website that will show the list of the files in my home folder.

i have look into the following sites shown below however was wondering is it the correct path that i am looking at.

[http://ubuntuforums.org/showthread.php?t=680619](http://ubuntuforums.org/showthread.php?t=680619)
[http://ubuntuforums.org/archive/index.php/t-347005.html](http://ubuntuforums.org/archive/index.php/t-347005.html)
[http://articles.slicehost.com/ubuntu-gutsy](http://articles.slicehost.com/ubuntu-gutsy)
 

hope someone can adivse how can i go about doing it.

thanks in advance.

---

### Post by dmonkey on 2009-08-26
If you want to view your home folder's files remotely using the internet, then you need to install a web server. The easiest (and best) is called apache. In principal, that is all that you need.

Apache will run from a folder on your computer called /var/www/. First, I would recommend that you put a subfolder here, called home, and then make this a link to your actual home directory:

ln -s ~/ /var/www/home

Make sure that apache is running, then in your web browser, go to

[http://localhost/home](http://localhost/home)

and there you should see a list of your home folder's files. If you want to access this from another computer using the internet, you have to allow incoming connections on the http port (80). And that should be it! You might not want everyone in the world to access your web page, so you can edit which ip addresses apache listens for in /etc/apache2/ports.conf. See 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

for more details.

---

### Post by calvinlyp on 2009-08-26
thanks dmonkey it was a detail piece of advise.

in fact i did install apache and i am lost what to do next.
but with your explainations i think i am getting some great info.

however one more doubt,
from what i quoted below:

> **dmonkey said:**
> 

Make sure that apache is running, then in your web browser, go to

[http://localhost/home](http://localhost/home)

and there you should see a list of your home folder's files. If you want to access this from another computer using the internet, you have to allow incoming connections on the http port (80). And that should be it! You might not want everyone in the world to access your web page, so you can edit which ip addresses apache listens for in /etc/apache2/ports.conf. See 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

for more details.

the [http://localhost/home](http://localhost/home) will show in the form of FTP view right?
in the sense, like this pic :
[http://en.flossmanuals.net/publish/MuSE/rsrc/MuSE/ftp.jpg](http://en.flossmanuals.net/publish/MuSE/rsrc/MuSE/ftp.jpg)

in fact actually my this web server at home contains multiple file of different dates.
thus was wondering can the listing the files generate out in a graphical manner.
like day1 contains 10 files
day2 contains 5 files etc.

thanks.please advise.
your help is greatly appreciated.

---

### Post by dmonkey on 2009-08-26
> **calvinlyp said:**
> thanks dmonkey it was a detail piece of advise.

in fact i did install apache and i am lost what to do next.
but with your explainations i think i am getting some great info.

however one more doubt,
from what i quoted below:

the [http://localhost/home](http://localhost/home) will show in the form of FTP view right?
in the sense, like this pic :
[http://en.flossmanuals.net/publish/MuSE/rsrc/MuSE/ftp.jpg](http://en.flossmanuals.net/publish/MuSE/rsrc/MuSE/ftp.jpg)

Yes that's right, you'll get exactly this view.

> 
in fact actually my this web server at home contains multiple file of different dates.
thus was wondering can the listing the files generate out in a graphical manner.
like day1 contains 10 files
day2 contains 5 files etc.

thanks.please advise.
your help is greatly appreciated.

This is possible, but not with Apache alone, you'll need a sever-side scripting engine, probably PHP is best. But I would say walk before you can run. Can you get the first part working?

---

### Post by calvinlyp on 2009-08-28
Hi dmonkey, first part already working fine. thanks for your help.

however is there a way to view other folder rather than only  /var/www ?
as i may want to look into other folders of directory within the localhost pc.

please advise.

---

### Post by dmonkey on 2009-09-03
> **calvinlyp said:**
> however is there a way to view other folder rather than only  /var/www ?
as i may want to look into other folders of directory within the localhost pc.

This is what I said above. You need to create a symbolic link in /var/www/ to any folders that you want to view, or, if you really want, you can change the directory that Apache treats as the web root.

---

