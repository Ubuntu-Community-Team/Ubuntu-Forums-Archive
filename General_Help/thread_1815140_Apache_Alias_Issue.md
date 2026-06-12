---
title: "Apache Alias Issue"
date: 2011-07-30
forum: General Help
---

### Post by OldManRiver on 2011-07-30
All,

I need to be able to run Apache again the folder in my /home directory.

I added the following line to the end of my apache2.conf file:

```
Include /etc/apache2/aliases.conf
```

Then created the aliases.conf file with:
```
Alias /home/ "/home/"
<Directory "/home/">
    Options Indexes
    AllowOverride All
    Order allow,deny
</Directory>
```

The system tries to process the alias, but always get a 403 permissions denied error.

How do I get around this?

I already tried:
```
chown myuser:users /home -R
chmod 775 /home -R
```

And has not helped.  Think it is an Apache setting I need to read in this directory.

Thanks!

OMR

---

### Post by fdrake on 2011-07-30
it's not a safe solution but i think you  have to completely make accessible the files to everyone else too.

```
sudo chmod -R 777 /home
```

---

### Post by bodhi.zazen on 2011-07-30
> **OldManRiver said:**
> All,

I need to be able to run Apache again the folder in my /home directory.

I added the following line to the end of my apache2.conf file:

```
Include /etc/apache2/aliases.conf
```

Then created the aliases.conf file with:
```
Alias /home/ "/home/"
<Directory "/home/">
    Options Indexes
    AllowOverride All
    Order allow,deny
</Directory>
```

The system tries to process the alias, but always get a 403 permissions denied error.

How do I get around this?

I already tried:
```
chown myuser:users /home -R
chmod 775 /home -R
```

And has not helped.  Think it is an Apache setting I need to read in this directory.

Thanks!

OMR

That is not how it is supposed to be done =)

See:

[http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file](http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file)

[http://bigbrovar.wordpress.com/2009/02/13/configure-apache-and-public_html-on-ubuntu/](http://bigbrovar.wordpress.com/2009/02/13/configure-apache-and-public_html-on-ubuntu/)

---

### Post by galvatron408 on 2011-07-30
NO, do not 777 your home directory! That's how you get hacked!

You're getting 403 because apache can't access your directory. You need to look at the apache log.

---

### Post by OldManRiver on 2011-07-31
> **bodhi.zazen said:**
> That is not how it is supposed to be done =)

See:

[http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file](http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file)

[http://bigbrovar.wordpress.com/2009/02/13/configure-apache-and-public_html-on-ubuntu/](http://bigbrovar.wordpress.com/2009/02/13/configure-apache-and-public_html-on-ubuntu/)

bodhi.zazen,

I used the HOWTO you gave at:

[http://bigbrovar.wordpress.com/2009/02/13/configure-apache-and-public_html-on-ubuntu/](http://bigbrovar.wordpress.com/2009/02/13/configure-apache-and-public_html-on-ubuntu/)

But when I go to:

[http://localhost/myuser/](http://localhost/myuser/)

or 

[http://localhost/home/](http://localhost/home/)

Still getting the 403 error.  I made sure I created the /home/myuser/public_html dir also.

OMR

---

### Post by bodhi.zazen on 2011-07-31
You need a ~ in there

[http://localhost/~your_user_name](http://localhost/~your_user_name)

---

### Post by OldManRiver on 2011-08-02
bodhi.zazen,

Same result with the '~'!

OMR

---

### Post by Doug S on 2011-08-02
The referenced tutorial mentions editing apche2.conf to add a UserDir line. That should not be needed. The "sudo a2enmod userdir" part will enable (after a restart or re-load of apache2) the file /etc/apache2/mods-available/userdir.conf which contains the needed stuff.
If it is still not working for you, what are the permissions on your public_html directory? On my system they are 755, as is my home directory.

---

### Post by galvatron408 on 2011-08-04
here, do this and it's ganna work...

ps -eaf | grep httpd

whoever owns the httpd process, chown your directory to that user.

---

### Post by OldManRiver on 2011-08-05
> **Doug S said:**
> The referenced tutorial mentions editing apche2.conf to add a UserDir line. That should not be needed. The "sudo a2enmod userdir" part will enable (after a restart or re-load of apache2) the file /etc/apache2/mods-available/userdir.conf which contains the needed stuff.
If it is still not working for you, what are the permissions on your public_html directory? On my system they are 755, as is my home directory.
DS,

Guess you didn't read, had already set to 775.

Cheers!

OMR

---

### Post by OldManRiver on 2011-08-05
> **galvatron408 said:**
> here, do this and it's ganna work...

ps -eaf | grep httpd

whoever owns the httpd process, chown your directory to that user.

galvatron408,

???

I run your cmd and get:
```
root      6760  6683  0 09:39 pts/0    00:00:00 grep --color=auto httpd
```
and "httpd" is in red.  What does this mean?

Thanks!

OMR

---

### Post by mbeach on 2011-08-05
have you restarted the service and tried:

[http://localhost/~myuser/](http://localhost/~myuser/)

---

### Post by Doug S on 2011-08-05
With the grep stuff, httpd is in red just to highlight the string match that caused grep to print the line. And, yes there is no httpd process running on my system either, but rather it is apache2 and the owner is www-data. The only reason any output from the grep command appears at all is because the command itself is an active process, and the grep match is basically matching itself.
 
When I mentioned permissions, I had read the entire thread, but there was some back and forth about permissions, so I wasn't sure you were still at 775. The permissions point I did not state well is that the permissions are first inherited from the higher levels. I.E. if the public_html folder is set to 755, but if the myuser parent directory, or even the home parent directory permissions are not right, then it will not work. On my system /home = 755, /home/doug = 755, /home/doug/public_html = 755.
What you are tyring to do should be one of the simpliest changes from the default, out of the box, settings. To bad you are having such troubles.

---

### Post by galvatron408 on 2011-08-06
wow, you must be really new to ubuntu but.... that's why we're here to try and help you.

and yea, I forgot, ubuntu renames httpd to apache, so search for apache and do what I said to do earlier

except, since I didn't know you were that new, you shoud do the following...

cd /home
sudo chown -R $user $user

replace $user with your user. This command will tell Linux to change the owner of the directory and everything in the directory. Be sure you don't run it incorrectly.

After that, you're going to have to make sure all directories and files have proper permission

This will tell linux add the permission rwx on the directory $user and all directories inside of $user
sudo find ./$user -type d -exec chmod u+rwx '{}' \;

This will tell linux to add r permission to all files inside the directory $user 
sudo find ./$user -type f -exec chmod u+r '{}' \;

After that, apache should no longer give you permission problems.

---

### Post by OldManRiver on 2011-08-14
All,

Was having major problems with this box over a network issue, so entirely wiped the disk and started over, now finally back to this issue.  I never got it working right before, so had done the work around by dropping everything I was working on into directories under /var/www.

Anyway, will probably get around to this later tonight, got some priority things first.

Quick note about me as noobie, no way, 11 years on Ubuntu, just never had Apache give me the berries before.  Thanks!

Cheers!

OMR

---

### Post by OldManRiver on 2011-08-23
All,

Thinking about this I remember there are two ways to resolve this:
[LIST=1]
[*]Get Apache Aliases working right
[*]Create dir under /var/www and build symlink to it to connect to real directory
[/LIST]
Prefer doing it the first/right way, but second will workaround so whatever is needed to get it going, without duplicate files.

Thanks!

OMR

---

### Post by OldManRiver on 2011-08-27
All,

OK one of the reasons for needing aliases, is I'm adding multiple frameworks to my box:
[LIST=1]
[*]CakePHP,
[*]CodeIgnitor,
[*]Drupal,
[*]Symphony,
[*]Zend.
[/LIST]
As I am writing certification tests and database for PHP programmers for levels 1-6:
[LIST=1]
[*]Interpretive (agree with Zend on this),
[*]OOP (Zend does not do this justice),
[*]Frameworks (mastery of 3 concepts and code - Zend only recognizes their own),
[*]Compiled PHP,
[*]Modular Design & Rad,
[*]Enterprise Modules.
[/LIST]
**Note:**
If you are not familiar with the last 3 will be glad to point you to resources.

I need the development area to be in a neutral non-www directory, so my work can essentially be developed in the equivalent to "Offline", then moved into the "www" world when I publish. 

I guess I'm impatient and want this now, but since I have not been able to debug it on my own, still working on it and waiting for responses that give me insight as to why it is not working right.

I been studying examples and wondering if I have to redeclare the DOCROOT for directories outside the /var/www directory.  Haven't wanted to change anything just yet, cause not sure if that will make the /var/www default DOCROOT dysfunctional.

If gotten a few more examples and going through them, but from what I read this is possible.

If you disagree, please chime in and say why!

Thanks!

OMR

---

### Post by bodhi.zazen on 2011-08-27
I would use virtual hosts and password protect a development directory.

---

### Post by galvatron408 on 2011-08-27
i don't like apache following symlinks. some how i always think its a bad idea, so i don't recommend symlinks to anyone.

---

### Post by OldManRiver on 2011-09-12
galvatron408/bodhi.zazen,

Agree with you both, but using all the samples I have, including code from working aliases from other machines, not able to make this work.

Any Ideas?

Thanks!

OMR

---

### Post by OldManRiver on 2011-09-28
All,

Seen no inputs on this now for 2 weeks.

Can I get some help?

OMR

---

### Post by OldManRiver on 2011-10-22
All,

Found one thing here and need your feedback on this.

I had put an include statement to the file which had the aliases, but it never worked.  When I added the same alias code to a file I knew was already being called the aliases worked.

What I am wondering, is does Apache, in some versions limit itself to just one include statement?  I ask this because multiples work on my WAMP install, but do not seem to work under Ubuntu, and wondering it this is a limitation of Apache or of Ubuntu?

Can I get some help here?

Thanks!

OMR

---

### Post by OldManRiver on 2011-12-07
All,

Can I get some help or feedback here?

OMR

---

### Post by OldManRiver on 2012-04-02
All,

Got my WebMin working and so now in control of this!

Closing as "SOLVED"!

Cheers!

OMR

---

