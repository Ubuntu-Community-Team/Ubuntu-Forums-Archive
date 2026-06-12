---
title: "make installation file executable"
date: 2010-07-03
forum: General Help
---

### Post by Odaym on 2010-07-03
I have downloaded the file "bitnami-wordpress-3.0-0-linux-installer.bin", it's a Wordpress stack, with PHP and apache and whatnot.. I am asked to make it executable using "chmod a+x <installer file>"
what do i do? cd to where it is, and "chmod a+x <bitnami-wordpress-3.0-0-linux-installer.bin>"?
and if yes, i just double click on it after that to run the installation?

thank you very much for your help! :)

---

### Post by stlsaint on 2010-07-03
run like this:
```
sudo chmod +x file.name
```

"DO NOT use <> around the file name"

then to execute it run enter the directory and run:

```
./file.name
```

---

### Post by Odaym on 2010-07-03
thank you very much, works :)

---

### Post by Odaym on 2010-07-04
when this worked last night, and i got it working, everything is fine.
but today i start and want to load the page i dont see anything on the 127.0.1.1 for example. I know that i need to load the webserver for the page to load, how do i do that? Wordpress uses Apache

---

### Post by Odaym on 2010-07-04
bump. please? :)

---

### Post by Odaym on 2010-07-05
help please? :) i dont even know what to type at search engines since this problem is scattered for me to really pin it down.

---

### Post by Leppie on 2010-07-05
to start the apache web server:
```
sudo service apache2 start
```

---

### Post by Odaym on 2010-07-05
im getting service unrecognized..

---

### Post by Leppie on 2010-07-05
could you post the output of the following command:
```
dpkg -l | grep -i apache
```

---

### Post by Odaym on 2010-07-05
> oday@Hive:~$ dpkg -l | grep -i apache
ii  apache2-utils                         2.2.14-5ubuntu8                                 utility programs for webservers
ii  libapr1                               1.3.8-1build1                                   The Apache Portable Runtime Library
ii  libaprutil1                           1.3.9+dfsg-3build1                              The Apache Portable Runtime Utility Library
ii  python-couchdb                        0.6-1                                           library for working with Apache CouchDB


you read of course that i downloaded this Wordpress stack along with its Apache and PHP and wordpress

---

### Post by Leppie on 2010-07-05
> **Odaym said:**
>  	 	 		 			 				> oday@Hive:~$ dpkg -l | grep -i apache
ii  apache2-utils                         2.2.14-5ubuntu8                                  utility programs for webservers
ii  libapr1                               1.3.8-1build1                                    The Apache Portable Runtime Library
ii  libaprutil1                           1.3.9+dfsg-3build1                               The Apache Portable Runtime Utility Library
ii  python-couchdb                        0.6-1                                            library for working with Apache CouchDB 
			 		you read of course that i downloaded this Wordpress stack along with its Apache and PHP and wordpress
well, you actually installed apache utils. however, the actual web server has not been installed. this is what the output looks like on a machine with apache installed:
```
dpkg -l | grep apache
ii  apache2                             2.2.14-5ubuntu8                   Apache HTTP Server metapackage
ii  apache2-mpm-prefork                 2.2.14-5ubuntu8                   Apache HTTP Server - traditional non-threade
ii  apache2-utils                       2.2.14-5ubuntu8                   utility programs for webservers
ii  apache2.2-bin                       2.2.14-5ubuntu8                   Apache HTTP Server common binary files
ii  apache2.2-common                    2.2.14-5ubuntu8                   Apache HTTP Server common files

```


to install apache:
```
sudo apt-get install apache2
```

---

### Post by btindie on 2010-07-05
Apache comes as part of the bitnami wordpress stack, it's nothing to do with the normal Ubuntu installed programs. As such it's not possible to control it in the normal Ubuntu way.
 
Have you read the [README]("http://bitnami.org/files/stacks/wordpress/3.0-0/README.txt") file that comes with it? From section 6 it tells you how to start/stop/restart the bitnami wordpress stack. In the main installation directory there should be a script called *ctlscript.sh*. From the installation directory run the following command to start it
```
./ctlscript.sh start
```

---

### Post by Odaym on 2010-07-06
> **btindie said:**
> Apache comes as part of the bitnami wordpress stack, it's nothing to do with the normal Ubuntu installed programs. As such it's not possible to control it in the normal Ubuntu way.
 
Have you read the [README]("http://bitnami.org/files/stacks/wordpress/3.0-0/README.txt") file that comes with it? From section 6 it tells you how to start/stop/restart the bitnami wordpress stack. In the main installation directory there should be a script called *ctlscript.sh*. From the installation directory run the following command to start it
```
./ctlscript.sh start
```

thank you very much, i should learn to be more aware of these help files and read them, and thank you Leppie

---

