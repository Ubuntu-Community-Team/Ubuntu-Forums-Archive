---
title: "Tried to install OTRS in Ubuntu 11.10, dbconfig failed, now apt is broken.."
date: 2012-04-24
forum: General Help
---

### Post by Spuds on 2012-04-24
Like the title says, I tried to install OTRS from repos.

During the setup, it tries to configure a database for OTRS, but it fails with:

An error occurred while installing the database:                                                                                                                                                                                                                                                                                            

> ERROR 1064 (42000) at line 1: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near      
'/usr/bin/mysql' at line 1                                                                                                                                                                                                                                                                                                                           

If at this point you choose "retry", you will be prompted with all the configuration questions once more and another attempt will be made at performing the operation.  
"retry (skip questions)" will immediately attempt the operation again, skipping all questions.  If you choose "abort", the operation will fail and you will need to  
downgrade, reinstall, reconfigure this package, or otherwise manually intervene to continue using it.  If you choose "ignore", the operation will continue, ignoring   further errors from dbconfig-common.       

I know that I'm using the right password-- if I try with the wrong password:

> ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

So I hit ignore because nothing was going anywhere... and it spits out this:

> populating database via sql...  done.
dbconfig-common: flushing administrative password
dbconfig-common: otrs2 configure: ignoring errors from here forwards
dbconfig-common: otrs2 configure: ignoring errors from here forwards
Module perl already enabled
Module rewrite already enabled
 * Reloading web server config apache2                                                                                                                                             Warning: DocumentRoot [/var/www/support2] does not exist
                                                                                                                                                                            [ OK ]
dpkg: error processing otrs2 (--configure):
 subprocess installed post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of otrs:
 otrs depends on otrs2 (>= 3.0); however:
  Package otrs2 is not configured yet.
dpkg: error processing otrs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 otrs2
 otrs

There's no database, so I know it didn't populate it.  Creating the database first doesn't help.

Now no matter what I try to do, I can't get rid of OTRS and every time I try to install a package, it tries to configure OTRS again.

Here's what I've tried:

> sudo apt-get remove --purge otrs*
sudo dpkg --configure -a
sudo apt-get install -f
sudo rm -rf /var/cache/apt/archives/*
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

And still the same problem.

Can anyone help?

I can install OTRS from scratch-- but thought I'd give the package a try.  :(  Bad move, apparently.

So no, I don't intend to keep this package.

Thanks VERY much in advance.

---

### Post by audiomick on 2012-04-24
This here
```
dpkg: dependency problems prevent configuration of otrs:
otrs depends on otrs2 (>= 3.0); however:
Package otrs2 is not configured yet.
```

looks like it might be the problem. It happens occasionally that a package depends on a different version of another package to the one in the repo. Shouldn't happen, but I've seen it a couple of times.

Have a look in the software centre/ synaptic and see what version of the package, if any, is installed. If it is not there, maybe try and install it alone and then try the other thing again. Don't know if that will help, but it is what I would try.

---

### Post by Spuds on 2012-04-24
Not sure how to change this to solved--

I installed aptitude and from the command line:

aptitude remove --purge otrs otrs2

And it worked like a charm.

So what's the difference between apt-get and aptitude?

Why would aptitude do what apt-get couldn't?

I'm no novice, but I do get stuck in my ways, and haven't truly given aptitude a chance.

I don't mind if I don't get an answer-- but pointing me towards aptitude did solve the problem.

-Spuds

---

### Post by audiomick on 2012-04-24
Here is the Wikipedia article on aptitude. I think the also explain the connection with apt-get.

[https://en.wikipedia.org/wiki/Aptitude_%28program%29]("https://en.wikipedia.org/wiki/Aptitude_%28program%29")

The option to mark as solved is under "thread tools" on the right at the top of the thread.

---

