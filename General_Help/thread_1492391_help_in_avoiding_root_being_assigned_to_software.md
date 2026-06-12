---
title: "help in avoiding root being assigned to software"
date: 2010-05-24
forum: General Help
---

### Post by blackhawx on 2010-05-24
I really don't mean to be annoyed but I am at this point...
I installed oscmax on ubuntu 10.04 and all the folders and files by default are owned by the root user.  But my ubuntu account is not a root account by default.  As a result I have no access to these files unless I do sudo su.  But even then...I have to MANAULLY go into every file and reassign it to my group? why?????  Is there an easy way to tell ubuntu that if I ever install a personal software application like oscmax to my /var/ or my /opt/ directory, to PLEEEASSE assign every folder and file in that package to MY group??? not root?

thanks :)

---

### Post by akakingess on 2010-05-24
I don't think so, if you are installing to the filesystem portion of Linux in any way, I think it is given the root ownership. I would personally either install it into your own user/home folder, or try to do something with some sym links, but they will even run into permission issues.

---

### Post by John Bean on 2010-05-24
> **blackhawx said:**
> I installed oscmax on ubuntu 10.04 and all the folders and files by default are owned by the root user.

You'll need to expand on that bit. Please explain in detail exactly what you did to install the software, then we'll have a clue as to what went wrong. Normally a correctly installed user program will not need to run as root.

---

### Post by blackhawx on 2010-05-24
ok, 
I wanted to install a local php/mysql/apache2 web server up.  so I went through the terminal and installed all 3.  The localhost directory now works, and is located in my var/www directory.  I tested it out [http://localhost/index.php](http://localhost/index.php) on my firefox  - works great. 

I downloaded to my desktop, oscmax from oscmax.com which is an open source ecommerce package.  I then uncompressed it because its initially zip file.  I then take my uncompressed oscmax folder and copy it to my var/www/demosite/ folder.  I then install oscmax through the www/demosite/catalog/install.php.  But almost everything is installed.  the oscmax install page "did not" create config.php automatically in var/www/demosite/catalog/includes, the way it normally does when i have done it under windows vista. Plus, the permissions to all the folders is assigned to root user and is read only.  As a result when i try to load up the demo site that comes with oscmax, the front page is blank (white).  thats because it wasnt allowed to automatically create the config.php file in its proper directory. I then I have to manually create that file in order to see the home page, but thats just the home page. every other file and folder under the software needs the same process (killer!!!).

There has to be a way to assign group access to read and write an entire software package, under "MY" group, not root.  this way when it installs, it installs correctly and you can read and write everything.

I like the idea of installing my localhost projects in aother directory, like under my home directory. but the million dollar question is how do you assign the apache2 web host to read that folder when it expects all php and db stuff to be under the var/www folder? :confused:

---

### Post by blackhawx on 2010-05-24
i just looked up a similar issue on another forum site - it looks like this is the answer to fix my permissions issue - 

```

$ sudo chown -R $USER:$USER /var/www

```

thanks peeps I'll let you know in a minute...

---

### Post by akakingess on 2010-05-24
You can change and give yourself permission to all of the www directory and all of it's subdirectories using the "chown" command (for exact options, I would look at man chown from the terminal), but you need to keep the /var/www where it is for server protection reasons/design, unless there is something that I don't know about Apache, but as far as server's go, that is why they are so protective.

EDIT: Just saw what you posted while I was typing.

---

### Post by blackhawx on 2010-05-24
that command gave my user ownership to www/var/ files - wooo!!!! but how can my group "not the owner" have the ability to create and delete files.  my group is www-data and its currently assigned to "access files" is that right or does that need to be adjusted. 

thanks again! :guitar:

---

### Post by akakingess on 2010-05-24
Again, I would do a man chown to look at the manual for chown on that one, I just can't remember the commands off of the top of my head and sometimes it helps you remember if you look it up on your own. Okay, now I am just being lazy ;(

---

### Post by Bobhuber on 2010-05-24
> **blackhawx said:**
> ok, 
I wanted to install a local php/mysql/apache2 web server up.  so I went through the terminal and installed all 3.  The localhost directory now works, and is located in my var/www directory.  I tested it out [http://localhost/index.php](http://localhost/index.php) on my firefox  - works great. 

I downloaded to my desktop, oscmax from oscmax.com which is an open source ecommerce package.  I then uncompressed it because its initially zip file.  I then take my uncompressed oscmax folder and copy it to my var/www/demosite/ folder.  I then install oscmax through the www/demosite/catalog/install.php.  But almost everything is installed.  the oscmax install page "did not" create config.php automatically in var/www/demosite/catalog/includes, the way it normally does when i have done it under windows vista. Plus, the permissions to all the folders is assigned to root user and is read only.  As a result when i try to load up the demo site that comes with oscmax, the front page is blank (white).  thats because it wasnt allowed to automatically create the config.php file in its proper directory. I then I have to manually create that file in order to see the home page, but thats just the home page. every other file and folder under the software needs the same process (killer!!!).

There has to be a way to assign group access to read and write an entire software package, under "MY" group, not root.  this way when it installs, it installs correctly and you can read and write everything.

I like the idea of installing my localhost projects in aother directory, like under my home directory. but the million dollar question is how do you assign the apache2 web host to read that folder when it expects all php and db stuff to be under the var/www folder? :confused:
You are going to have to get used to files and permissions in using Ubuntu and Linux. Its a different world.Where did you unzip it ? Did you unzip it thru the terminal as root ?
I STILL have problems after a year of using Ubuntu and setting up my own sever but most of them are because I don't follow the rules or have changed the environment to suit my needs.No passwords - Sudo etc. and a nasty shortcut that opens up a root terminal. The best advise starting out is don't do anything as root (Sudo or Gksu) unless you have to and put everything in your home directory.Of course this will change and your off to a great start in setting up your server.Its all part of the fun and frustration in using the operating system.As far as the Apache2 web host is concerned you WANT everything to be in the WWW folder that is run as host (PHP,HTML etc.)The system files required by MYSQL,PHP and the server will be automatically serviced by the server.
You can change the web directory to anything you want (mine is home/bob/webpages) by changing the server setup.

---

### Post by blackhawx on 2010-05-24
> **Bobhuber said:**
> You are going to have to get used to files and permissions in using Ubuntu and Linux. Its a different world.Where did you unzip it ? Did you unzip it thru the terminal as root ?
I STILL have problems after a year of using Ubuntu and setting up my own sever but most of them are because I don't follow the rules or have changed the environment to suit my needs.No passwords - Sudo etc. and a nasty shortcut that opens up a root terminal. The best advise starting out is don't do anything as root (Sudo or Gksu) unless you have to and put everything in your home directory.Of course this will change and your off to a great start in setting up your server.Its all part of the fun and frustration in using the operating system.As far as the Apache2 web host is concerned you WANT everything to be in the WWW folder that is run as host (PHP,HTML etc.)The system files required by MYSQL,PHP and the server will be automatically serviced by the server.
You can change the web directory to anything you want (mine is home/bob/webpages) by changing the server setup.

You rock man! thanks for the tip - I'm currently loading all my web projects in into var/www/ as recommeneded - but do you happen to know how we can change like this... [http://locahost/devsite](http://locahost/devsite) to [http://dev.site?](http://dev.site?)  I'm so use to doing it in the vhost file under xampp for several years. but is there a way to give that directory a virtual name alias?

ALSO I FOUND MY SOLUTION!!!! WOO!!! that code about i wrote was the begining step to assign my user to access www/var.  the second step is that once the oscmax is unziped in your directory, click the catalog folder to assign "create and delete files" group permissions to that folder AND the files under it.  Then go into the the admin folder and repeat the same process.  THEN install oscmax!! var/www/demosite/catalog/install/    and then you'll be able to access and load everything correctly.  its like a dream!!! WOOO!!! So yes you are right friend, permissions is a different world here!

bh :popcorn:

how o mark this post as solved?

---

### Post by Bobhuber on 2010-05-25
> **blackhawx said:**
> You rock man! thanks for the tip - I'm currently loading all my web projects in into var/www/ as recommeneded - but do you happen to know how we can change like this... [http://locahost/devsite](http://locahost/devsite) to [http://dev.site?](http://dev.site?)  I'm so use to doing it in the vhost file under xampp for several years. but is there a way to give that directory a virtual name alias?

You haven't even scratched the surface yet with setting up and servicing an apache2 Server. Start here > [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) for the basics which you have a good start on. It has links on the bottom of the page for setting up Virtual Host subdomains. Then here > [http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/) for the full blown documentation. If you can digest it all in a couple of months check back and I'll have questions for YOU to answer. LOL

---

### Post by blackhawx on 2010-05-25
Thanks for the links Bohuber. I do admit, I have a lot to learn but I have already completed all steps under the ubuntu apache page you posted.  By the way, I found the solution to setting up virtual host names and found a solution for that terminal warning of overlapping virtual host names too! that was a killer but with some patience and skill and reading like you said,  it all works out :).  I'm only gonna be using my apache for a development platform.  But I'll keep reading though!  

Thanks again

---

### Post by akakingess on 2010-05-25
@blackhawx  -  > how o mark this  post as solved? 		                   		  		  		  		  		 		

You go to the "Thread Tools" at the top of this thread and should be able to mark it as solved from there, and only you as the OP (original poster) can do so. Keep in mind, it won't delete the thread, so you can refer back to it later if needed, but it at least helps the rest of the community know that no more assistance is needed. Good Luck and Have Fun, I think that you will end up LOVING Ubuntu, as I have ;)

---

