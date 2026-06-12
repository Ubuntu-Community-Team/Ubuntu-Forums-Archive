---
title: "php pear seems broken"
date: 2011-05-02
forum: General Help
---

### Post by ndefontenay on 2011-05-02
Hi.

I'm trying to install a package (validate) from pear.

but the command sudo pear install validate fails with error:

PHP Fatal error:  Call to undefined method PEAR::raiseErro() in /usr/share/php/PEAR/REST.php on line 165 

Looking around on the internet I found a bug report on debian:
[http://groups.google.com/group/linux.debian.bugs.rc/browse_thread/thread/f7a58c7aff4741a2?pli=1](http://groups.google.com/group/linux.debian.bugs.rc/browse_thread/thread/f7a58c7aff4741a2?pli=1)

The fix is to update php5.

So now the question:

How do I update php5 or apply the patch mentioned in this bug report?

---

### Post by grossvogel on 2011-05-04
I'm having the same issue. Not only is the package fetch failing, but there's a typo in the error handling code!?!

I fixed the typo as follows:
[PHP]raiseErro() => raiseError()[/PHP]


Now I see the following error:
> No releases available for package "pecl.php.net/[package]"
Cannot initialize 'channel://pecl.php.net/[package]', invalid or missing file
Package "channel://pecl.php.net/[package]" is not valid
install failed

**EDIT**
I checked out the patch discussed on the debian thread, and it does nothing but the typo fix I listed above. I suppose we should check out Launchpad and hopefully the php5 patch will get added to the repos soon.
[B]
EDIT II[/B]
OK, here's a bug that appears to address this issue. I haven't had 100% success with this (ERROR: 'phpize' failed), but it's a start. [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/774452]("https://bugs.launchpad.net/ubuntu/+source/php5/+bug/774452") Basically, it's failing to create /tmp/pear/cache, so you can avoid the error if you create the directory on your own first.

---

### Post by aWbrook on 2011-05-04
Thanks for the pointer, it worked for me.  I'm continually amazed by the useful information people take the time to post - so maybe this can help someone else trying to get xdebug working on ubuntu 11.04 lamp server.   After installing lamp-server I was unable to install xdebug because of this bug.  Fixed as follows:

```
sudo mkdir /tmp/pear
sudo mkdir /tmp/pear/cache

```Then I was able to successfully  ...

```
sudo pecl install xdebug
```

---

### Post by grossvogel on 2011-05-05
It looks like the fix hit the repos today.

---

### Post by rodrigosprimo on 2011-05-05
After updating today both xdebug and pear are back to normal on my machine.

---

