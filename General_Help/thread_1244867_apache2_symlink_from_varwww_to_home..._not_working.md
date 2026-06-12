---
title: "apache2 symlink from /var/www to /home... not working"
date: 2009-08-19
forum: General Help
---

### Post by Zeroangel on 2009-08-19
Hi all,

I'm doing some web development on my Linux Mint machine and i'm having some trouble with apache. 

This time I installed Apache2 through the Synaptic -> Mark Packages by Task -> LAMP Server method.

After installing apache what I normally do is

```
rmdir /var/www

ln -s /home/me/Webdev/Projects /var/www

chmod -R 777 /var/www 
```And normally I can edit my websites without having to go outside of my home folder or deal with permissions.

However this time it does not work

Whenever I try to view any document (including JPEG images) on localhost, I get the following screen > **Forbidden** 
You don't have permission to access /solitaryweb/index.php on this server.
  Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch Server at localhost Port 80[/i]/var/www/apache2/apache2.log outputs the following:
> david@archangel-linux /var/log/apache2 $  cat error.log
[Mon Aug 17 20:04:54 2009] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations
[Mon Aug 17 20:05:03 2009] [notice] Graceful restart requested, doing restart                      
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Mon Aug 17 20:05:03 2009] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations           
[Mon Aug 17 20:29:27 2009] [notice] caught SIGTERM, shutting down                                             
[Mon Aug 17 20:30:27 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Aug 17 21:13:44 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:13:44 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:13:47 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:14:48 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:14:48 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:14:49 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:14:54 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:16:27 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:17:17 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:17:19 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:17:20 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:18:07 2009] [notice] caught SIGTERM, shutting down                                                                          
[Mon Aug 17 21:18:08 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Aug 17 21:18:12 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:18:12 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:18:13 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:18:13 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:18:13 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:19:30 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:19:32 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:19:33 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:21:29 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:21:32 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:22:51 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
[Mon Aug 17 21:25:27 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www                    
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0                                                                                                                                                         
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mcrypt.so' - /usr/lib/php5/20060613+lfs/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0                                                                                                                                                 
[Tue Aug 18 01:54:44 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations                                         
[Tue Aug 18 01:56:20 2009] [notice] caught SIGTERM, shutting down                                                                                                                   
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0                                                                                                                                                         
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mcrypt.so' - /usr/lib/php5/20060613+lfs/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0                                                                                                                                                 
[Tue Aug 18 01:58:19 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations                                         
[Tue Aug 18 01:58:32 2009] [notice] caught SIGTERM, shutting down                                                                                                                   
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0                                                                                                                                                         
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mcrypt.so' - /usr/lib/php5/20060613+lfs/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0                                                                                                                                                 
[Tue Aug 18 11:30:13 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations                                         
[Tue Aug 18 13:00:11 2009] [notice] caught SIGTERM, shutting down                                                                                                                   
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0                                                                                                                                                         
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mcrypt.so' - /usr/lib/php5/20060613+lfs/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0                                                                                                                                                 
[Tue Aug 18 15:36:47 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations                                         
[Tue Aug 18 15:39:37 2009] [notice] caught SIGTERM, shutting down                                                                                                                   
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mcrypt.so' - /usr/lib/php5/20060613+lfs/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Wed Aug 19 18:04:19 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Aug 19 20:43:51 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:43:51 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:43:54 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:47:30 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:49:08 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:49:09 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:49:42 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:49:43 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:49:43 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:49:43 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:50:41 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:50:42 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:51:15 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:51:16 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:51:16 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:51:16 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:51:16 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:51:17 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:51:17 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Wed Aug 19 20:51:17 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/wwwI've verified that I am the owner and group of the folders, and applied the permission recursively, with R/W/X access given to 'other', so it shouldnt matter.

Any ideas?

---

### Post by mthalis on 2009-08-19
I think this help you.
[http://www.netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#specifyDocumentRoot](http://www.netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#specifyDocumentRoot)

---

### Post by dfreer on 2009-08-19
> On Unix systems, symbolic links can bring other parts of the filesystem under the DocumentRoot. For security reasons, Apache will follow symbolic links **only if the Options setting for the relevant directory includes FollowSymLinks or SymLinksIfOwnerMatch.**
From [http://httpd.apache.org/docs/2.0/urlmapping.html](http://httpd.apache.org/docs/2.0/urlmapping.html)

---

### Post by Zeroangel on 2009-08-19
Well, i've edited /etc/apache2/sites-available/default to point to the proper directory instead of a symlinked version of it. I've disabled and re-enabled the default vhost, restarted apache. Still. The problem remains.

Anyone have any more ideas?

---

### Post by Zeroangel on 2009-08-19
Problem solved. It was due to the fact that I had restored the site from a backup which was on an NTFS volume.

/home/david/Webdev/Projects had 777 permissions for the directory and files

yet

/home/david/Webdev -- permissions were set up to deny access to 'other' (740)

I gave /home/david/Webdev recursive 744 permissions and now the problems are gone!

---

