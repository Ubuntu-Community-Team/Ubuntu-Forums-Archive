---
title: "WEBDAV User right management"
date: 2010-11-08
forum: General Help
---

### Post by mrchrister on 2010-11-08
Hey guys,
i need a little help with webdav

I was able to setup webdav on my ubuntu server using the official ubuntu guide:
[http://wiki.ubuntuusers.de/Apache/webdav](http://wiki.ubuntuusers.de/Apache/webdav)

Everything works like a charme and i can also upload files this way.
only one problem:

Uploaded files via webdav have these rights:
-rw------- 1 www-data www-data

How can I change the upload user or at least make the files available to the group upon upload?

---

### Post by mrchrister on 2010-11-08
things i tried:
1. added "umask 002" to /etc/apache2/envvars and restart Apache.


files are still:
-rw------- 1 www-data www-data 42725 2010-11-09 01:00 Screen shot 2010-10-29 at 01.14.27.png


2. umask 022 in /etc/profile

result: files are still not group writeable

---

### Post by mrchrister on 2010-11-09
bump... nobody uses webdav here?

---

### Post by mrchrister on 2010-11-09
noone?

---

### Post by SeijiSensei on 2010-11-09
A clunky method would be to run "chmod g+w -R /var/www/webdav" in /etc/crontab once a minute.  

[This approach]("http://mike.kruckenberg.com/archives/2004/05/change_file_per.html") might also work; you'd need to change /etc/init.d/apache2 on Ubuntu.

---

### Post by mrchrister on 2010-11-09
thanks sensei!!
i also had the crontab idea, but it would waste system resources unnecessarily . i'm gonna check your second link now!

cheers,
chriss

---

### Post by mrchrister on 2010-11-09
update: i added the line umask 022 at the end of apache2 file

unfortunately it didnt change anything :(
files still have the mentioned rights..

---

### Post by mrchrister on 2010-11-09
bump

---

### Post by mrchrister on 2010-11-10
sorry to bump this thread so much... i really hope i'm gonna find someone who knows a bit about webdav! it seems like my thread is buried within minutes :)

---

### Post by SeijiSensei on 2010-11-10
> **mrchrister said:**
> thanks sensei!!
i also had the crontab idea, but it would waste system resources unnecessarily . i'm gonna check your second link now!

cheers,
chriss

That approach won't "waste" anything.  It's a simple command that executes in milliseconds.

---

### Post by mrchrister on 2010-11-10
but by checking it would access the hard drive...
i  guess this method is a bit too dirty mate ;)
but theanks for the suggestion I appreciate it!

---

### Post by mrchrister on 2010-11-12
who could i ask about webdav in ubuntu? any suggestion?

---

### Post by mrchrister on 2010-11-17
bump.

---

### Post by keyslapper on 2010-12-07
In addition to yet another bump, I wanted to point out the steps I've taken.

Most of the links I've found suggest adding the "umask 002" command to the /etc/init.d/apache2 startup script.  I'm guessing that, like me, everyone bumping this thread has tried that to no avail.

I've also tried adding this to /usr/sbin/apache2ctl script, which didn't work.  Neither did creating ~www/.profile and adding the umask line to it.

I'm averse to adding this to /root/.profile or /etc/.profile as it seems far too broad a brush for this job.  I have my doubts about whether it would work anyway.

I have tried looking at httpd.apache.org, but there's nothing mentioned about this issue.  I'm guessing that the latest versions of Apache are overriding the default umask, but I hope I'm wrong.  If it comes down to it, I'll probably just grab the source and see if the mod_dav module is forcing its own mask.  If so, only a code patch is going to correct this.

The primary reason I'm not doing this already, is that there are still a lot of threads out there saying the "umask 002" fix is still working for CentOS, RH, and Fedora, among other distributions.

If I find anything useful, I will certainly post it here in this thread.

Cheers.

---

### Post by mrchrister on 2010-12-08
Hey keyslapper, thanks so much for posting this! I tried all these "solutions" myself and it didnt work! I'm also expecting the dav module to have its own umask!
I'm still looking for a solution so if you find out anything please let me know!
Much appreciated, chriss!

---

### Post by keyslapper on 2010-12-08
I gave up looking for a config and went looking at the apache2 source.  The dav modules are part of the source package, so I got direct access to that as well.

The webdav module is using the APR open routine (apr_file_open()).  I found the following interesting bit in apr_file_io.h:

```

...
 * @param perm Access permissions for file.
 * @param pool The pool to use.
 * @remark If perm is APR_OS_DEFAULT and the file is being created,
 * appropriate default permissions will be used.
 * @remark By default, the returned file descriptor will not be
 * inherited by child processes created by apr_proc_create().  This
 * can be changed using apr_file_inherit_set().
 */
APR_DECLARE(apr_status_t) apr_file_open(apr_file_t **newf, const char *fname,
                                        apr_int32_t flag, apr_fileperms_t perm,
                                        apr_pool_t *pool);

```

as far as I can tell, APR_OS_DEFAULT is being used, and inside apr_file_open, this translates to using 0666 as a mode in the unix open (2) call.

This suggests that the default mask for the user running Apache is in fact 077 - no group or other access.

Unfortunately, that doesn't jive with the following experiment I just ran on my server:

```
[FONT=monospace]
[/FONT]# su - www[FONT=monospace]
[/FONT]$ umask[FONT=monospace]
[/FONT]0002[FONT=monospace]
[/FONT]$ cd /tmp/[FONT=monospace]
[/FONT]$ touch tmp.txt[FONT=monospace]
[/FONT]$ ls -l[FONT=monospace]
[/FONT]total 0[FONT=monospace]
[/FONT]-rw-rw-r-- 1 www www 0 Dec  8 21:45 tmp.txt[FONT=monospace]
[/FONT]$

```

This suggests that either Ubuntu, Apache, or mod_dav is mucking with the default at some point.  I still can't tell where.

I'm not sure if I should report a bug.  Or if I do, who do I report it to, Apache or Ubuntu?  This still doesn't seem to be a problem with other distros (CentOS, RH, Suse, etc.) so I'm leaning toward Ubuntu.

---

### Post by mrchrister on 2010-12-11
Interesting find! Indeed it seems like ubuntu is not using the os default at some point!
is the webdav user www for you? mine is www-data...

the same experiment with www-data reveals for me:
su - www-data
$ bash
www-data@xxx:~$ umask
0022
www-data@xxx:~$ cd /tmp/
www-data@xxx:/tmp$ touch tmp.txt
www-data@xxx:/tmp$ ls -l
-rw-r--r-- 1 www-data www-data    0 2010-12-11 13:25 tmp.txt


so the group and other at least get reading permissions... but not for the stuff uploaded via webdav!
this still has:
-rw-------  1 www-data www-data

---

### Post by keyslapper on 2010-12-14
Yes, www-data is the default (on Ubuntu).  I prefer www, probably because that's what it is on FreeBSD, probably because it seems more concise to me.

Either way, thank you.  I'm glad to have confirmation that I'm not crazy.  At least not about this.

Judging from all the other threads out there discussing this, it's something that is easily fixed for other OSes and even other Linux distros.  In fact, Ubuntu is the ONLY platform I can confirm this won't fix the problem for.

This suggests there's something wonky in the way Ubuntu is handling this.  But this experiment suggests Ubuntu is doing the right thing at the filesystem level with respect to umask settings.  Perhaps it's just the configuration of the Apache package?

I wonder if there's a patch being applied by Ubuntu or Debian that breaks this somehow.

Perhaps this weekend I'll get a stock build of Apache on a VM here and see if the madness continues.  If that fixes it, perhaps the source diff will reveal the problem.

Cheers!

---

### Post by mrchrister on 2010-12-15
Thanks for looking into this problem keyslapper. It seems like the right way to go to compile apache from source and see if this changes something!

---

### Post by smonsarr on 2011-01-04
Hi, Just to say that I am having the exact same problem on a server running 10.04.
I upgraded a month ago from 8.04 that did not have this problem, webdav uploaded files in 8.04 honored the default umask.

This seems to be a bug in Ubuntu's Apache/webdav implementation that we should report.

---

### Post by mrchrister on 2011-01-15
any news on this issue? could somebody check with the method above if this is different in 10.10?

---

### Post by mrchrister on 2011-03-07
is the webdav user rights issue fixed in the new ubuntu release?

---

### Post by lil_elvis2000 on 2011-03-11
Has someone logged a bug for this or found out what is going on?

My users are quite annoyed as I had moved "up" from lighttpd to Apache for webdav. Lighttpd respected the directory defaults and ACL defaults perfectly.

I now probably have to go back to lighttpd until apache is fixed or someone has a setting that does the trick.

Edit: I found this in launchpad. [https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/540747](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/540747). It does appear this has been known for some time. I looks like it should be okay for 10.10 but 10.04 is toast.

---

### Post by mrchrister on 2011-03-14
Thanks for the input lilelvis!
I think I'll upgrade to 10.10 now!

---

### Post by mrchrister on 2011-03-15
After having some issues with apache after upgrading to 10.10 I can confirm that the issue is not there anymore in 10.10 (yey!)

---

### Post by lil_elvis2000 on 2011-03-15
Good stuff. I only go up by LTS so this really is quite annoying. Perhaps it will be backported to 10.04 in April? though no further notes in Launchpad about this yet.

So for the moment I'm using a crontab script to find files with the improper perms and update them every five minutes.

---

