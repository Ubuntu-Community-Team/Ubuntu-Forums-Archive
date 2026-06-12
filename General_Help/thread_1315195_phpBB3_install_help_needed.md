---
title: "phpBB3 install help needed"
date: 2009-11-05
forum: General Help
---

### Post by dfro on 2009-11-05
I set up a LAMP stack on ubuntu 9.10. The root directory of apache2 is at /var/www.

I tried setting up phpBB3 using synaptic. It created the database 'phpbb3' in mysql (good!), but it failed to put or link anything in /var/www. So, when I go to 'http://localhost/phpBB3' in firefox, I get nothing. It seems that synaptic put phpbb3 in /usr/share. 

I have read '/usr/share/doc/phpbb3/README.Debian'

But, I cannot figure out what this statement means at the beginning of the document:

2) Make sure you include /etc/phpbb3/apache.conf in the apache config of
your choice, for example by creating a symlink from etc/apache(2)/conf.d
to it. Usually, phpbb3 should have asked you to do this for you during
configuring.


IMHO, this is very poorly written! Could someone explain in better english how I can get apache2 to find phpbb3?

Thanks,
Dave

---

### Post by geoffmcc on 2009-11-05
to be honest with you I am not sure how to install the way you have done, but since i currently have it going i thought maybe i might suggest installing it manually.

I have webmin installed so i used that to create my phpbb database, can also be done pretty easily in phpmyadmin. once database is created wget the phpbb files and extract. move phpbb folder to /var/www

navigate to yourdomain.com/phpbb and follow the easy install script. I always chmod 755 the directory so owner and group (www-data) have read write execute, the install script may also tell you some files are unreadable, if it does chmod 755 them

hope that helps

---

### Post by dfro on 2009-11-05
Thanks for the reply.

I thought the whole point of synaptic was to streamline the install/update/uninstall process. It is very strange that I cannot get any info on the web on how to get the synaptic phpbb3 package working. 

The synaptic package did create a 'phpbb3' database in my mysql installation, which is good. But, I find it very curious that there is no part of the install process that gets apache2 finding phpbb3.

I will wait a day or so and see if someone else has some more info. Otherwise, I will give up on the .deb package and its cryptic (at least to a noobie) README.Debian file and do a manual install.

Thanks,
Dave

---

### Post by dfro on 2009-11-05
I have made a little progress.

I found this post, which helped:

[http://www.phpbb.com/community/viewtopic.php?f=46&t=1296455](http://www.phpbb.com/community/viewtopic.php?f=46&t=1296455)

I ran the command 'sudo ln -s /usr/share/phpbb3/www/ /var/www/phpbb3' to create a symbolic link. The ln command did not work if I wrote '/var/www/phpbb3/' with the '/' at the end. I got an error saying that /var/www/phpbb3 is not a directory - or something like that.

So, now when I direct firefox to 'localhost/phpbb3' is get a page that says:

Your new phpBB board
Powered by Debian

Information

Sorry but this board is currently unavailable.
______________________________________________

I don't think I want an 'unavailable' phpBB board 'Powered by Debian' - whatever that means. I will be doing a manual install. I hope it works.

Dave

---

### Post by phillw on 2009-11-05
> **dfro said:**
> I set up a LAMP stack on ubuntu 9.10. The root directory of apache2 is at /var/www.

I tried setting up phpBB3 using synaptic. It created the database 'phpbb3' in mysql (good!), but it failed to put or link anything in /var/www. So, when I go to 'http://localhost/phpBB3' in firefox, I get nothing. It seems that synaptic put phpbb3 in /usr/share. 

I have read '/usr/share/doc/phpbb3/README.Debian'

But, I cannot figure out what this statement means at the beginning of the document:

2) Make sure you include /etc/phpbb3/apache.conf in the apache config of
your choice, for example by creating a symlink from etc/apache(2)/conf.d
to it. Usually, phpbb3 should have asked you to do this for you during
configuring.


IMHO, this is very poorly written! Could someone explain in better english how I can get apache2 to find phpbb3?

Thanks,
Dave

Don't use Synaptic to install phpBB3  :mad:

::SIGH::   No idea why it doesn't work, but, it just doesn't.

Mine and a couple of others experience is listed over here --->>>>[http://ubuntuforums.org/showthread.php?t=986657&highlight=phillw](http://ubuntuforums.org/showthread.php?t=986657&highlight=phillw)

Don't forget the link we all used :p

[http://www.phpbb.com/support/documentation/3.0/](http://www.phpbb.com/support/documentation/3.0/)

Get synaptic to un-install it's version of phpBB before you do the new install.

My Cry for help is over here --->>>  [http://www.phpbb.com/community/viewtopic.php?f=46&t=1694645](http://www.phpbb.com/community/viewtopic.php?f=46&t=1694645)

/edit ... someone has updated the thread at phpbb ... r ead the bit at the end of it !!!!!  (I wish someone had told me earlier !!!!)

There are some of my musings on the prevention of forum spammers & general 'bad - people' over here --> [http://www.vpolink.com/showthread.php?p=3443](http://www.vpolink.com/showthread.php?p=3443)

Phill.

---

### Post by dfro on 2009-11-05
phillw,

Thanks for the info. While trying to figure things out earlier, I did read that first ubuntu forum thread that you started and it made my head spin.

I just read your thread on the phpbb.com forum. I have to laugh at the last reply:


Re: Start phpBB3 - from a BB newb

Postby hombibi » Fri Oct 16, 2009 9:43 am
The synaptics installer does work, it installs phpBB3, sets it up AND than sets the Board to "disabled". You see the result of that on the screen you mentioned with "Welcome to your new board" followed by Sorry but this board is currently unavailable." The trick is to login. You can login with username admin and password admin. After that you have to logon to the Adminstator Control Panel with the same username and password and navigate to General > Board Settings > Disable Board and set it to "no". With that the problem is solved.
There is not need for removing installation folders, that is done already, maybe by the synaptic package maintainers.
-------------------------------------------------------------------------

Does that seem obvious to you??!!! Talk about cryptic!! Without some better documentation written in plain english in a file that is easily found, the deb/synaptic package of phpbb3 is unusable, IMHO. Sorry, about the flames.

I did get a manual install working. I removed the phpbb3 package and manually deleted the phpbb3 database from mysql. And manually created a new phpbb3 database:

mysql>DROP DATABASE phpbb3;
mysql>CREATE DATABASE phpbb3;

After downloading the current phpbb3*.zip file from phpbb.com, I had to manually extract it, since the automatic extractor would not do it. 

I moved the new phpBB3 directory from /tmp/phpBB3 to /var/www/phpBB3.
I then followed the directions here, under "1. Quick install" to change some of the permissions on some of the files:

[http://netenberg.com/phpBB/docs/INSTALL.html](http://netenberg.com/phpBB/docs/INSTALL.html)

Then I directed firefox to "http://localhost/phpBB3" and phpbb3 launched into the automatic install, which went without a hitch. Very smooth!

Edit: After the install I deleted the /var/www/phpBB3/install folder. A big red warning message on the new forum page told me to do it. As soon as I deleted the file, the warning went away.

Thanks geofmcc and phillw for the comments and help,
Dave

---

### Post by phillw on 2009-11-05
> **dfro said:**
> phillw,

Thanks for the info. While trying to figure things out earlier, I did read that first ubuntu forum thread that you started and it made my head spin.

I just read your thread on the phpbb.com forum. I have to laugh at the last reply:


Re: Start phpBB3 - from a BB newb

Postby hombibi » Fri Oct 16, 2009 9:43 am
The synaptics installer does work, it installs phpBB3, sets it up AND than sets the Board to "disabled". You see the result of that on the screen you mentioned with "Welcome to your new board" followed by Sorry but this board is currently unavailable." The trick is to login. You can login with username admin and password admin. After that you have to logon to the Adminstator Control Panel with the same username and password and navigate to General > Board Settings > Disable Board and set it to "no". With that the problem is solved.
There is not need for removing installation folders, that is done already, maybe by the synaptic package maintainers.
-------------------------------------------------------------------------

Does that seem obvious to you??!!! Talk about cryptic!! Without some better documentation written in plain english in a file that is easily found, the deb/synaptic package of phpbb3 is unusable, IMHO. Sorry, about the flames.

I did get a manual install working. I removed the phpbb3 package and manually deleted the phpbb3 database from mysql. And manually created a new phpbb3 database:

mysql>DROP DATABASE phpbb3;
mysql>CREATE DATABASE phpbb3;

After downloading the current phpbb3*.zip file from phpbb.com, I had to manually extract it, since the automatic extractor would not do it. 

I moved the new phpBB3 directory from /tmp/phpBB3 to /var/www/phpBB3.
I then followed the directions here, under "1. Quick install" to change some of the permissions on some of the files:

[http://netenberg.com/phpBB/docs/INSTALL.html](http://netenberg.com/phpBB/docs/INSTALL.html)

Then I directed firefox to "http://localhost/phpBB3" and phpbb3 launched into the automatic install, which went without a hitch. Very smooth!

Thanks geofmcc and phillw for the comments and help,
Dave

:lolflag::popcorn:

It's a good idea to remove the install folder from the area that has your BB on.  I found phpBB to be very good, and the support site is really good. To cut down on 'baddies' I'd suggest turning on the stopforumspam part of it. It's in the admin area.

Happy forum, I may track you down & pop on some time ;)

Phill.

---

### Post by dfro on 2009-11-05
phillw,

Thanks for the info. I now realize that I will have to study how to guard against cyber-attacks on website forums, if I plan to get a forum site online.

I forgot to mention in my previous post that I did delete the '/var/www/phpBB3/install' folder. As soon as I did it the big red warning message on my new phpBB3 site went away. Another clear, helpful aspect of the manual install process. I'll add that to the previous post.

Thanks,
Dave

---

### Post by phillw on 2009-11-07
> **dfro said:**
> phillw,

Thanks for the info. I now realize that I will have to study how to guard against cyber-attacks on website forums, if I plan to get a forum site online.

I forgot to mention in my previous post that I did delete the '/var/www/phpBB3/install' folder. As soon as I did it the big red warning message on my new phpBB3 site went away. Another clear, helpful aspect of the manual install process. I'll add that to the previous post.

Thanks,
Dave


We're in the middle of updating the forum that I'm an admin on. I have a thread kicking around that I will try to keep updated over here ---->>> [http://www.vpolink.com/showthread.php?t=2487](http://www.vpolink.com/showthread.php?t=2487)

Follow the rules that Bhodi has taken the time to do, follow the links that are on that posting. If you **DO** decide to put a forum on-line, be prepared for saddos attacking you.

Code-call are a real nice set of people for stuff, but the phpBB forum will be best able to answer questions on reducing the success rate of 'bad people'.

You will find that you become a member of various sites to help protect you, to try and take some of the work load off our site owner, I have spent a lot of hours getting resources together to help out on our site. 

Once you are seen to be a genuine person, there is great help to be found for those who maintain Forums. Just be aware, it is a really big undertaking.

If you want any help on things, I'll be happy to offer you any assistance that I can.

And, if you'd like to have this email drop into your mail box -->> [B][http://www.vpolink.com/blog.php?b=33](http://www.vpolink.com/blog.php?b=33)

[/B]I'd be more than happy to tell you, or anyone, how they can help out for the volunteer sites to have good, upto date information that we can all use to help stop the menance.

Phill.

---

