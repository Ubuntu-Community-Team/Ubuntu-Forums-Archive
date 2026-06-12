---
title: "how do i use php function  system() as sudo?"
date: 2010-06-03
forum: General Help
---

### Post by Crdir on 2010-06-03
I need to  print the mail queue out  using     system(mailq)

I tested system(date) and my page lists the date, but I need to be able to do some sudo commands via php. Any ideas? been on this for hours im stuck.

Thanks

---

### Post by tufcamman on 2010-06-03
I've always used shell_exec() function and it has performed nicely.

[http://php.net/manual/en/function.shell-exec.php](http://php.net/manual/en/function.shell-exec.php)

You could write a bash script that included the neccesary sudo functions, and then execute it using that fuction.  Just be sure to make the script executable (chmod +x).

A few things though, you would need to grant the apache user (found in /etc/apache2/envvars www-data by default) sudo access (done using visudo) also this would have to be passwordless access (not very secure) in order for php to execute a shell script with sudo commands.

Also, shell_exec() requires that some safe modes be turned off in php, ubuntu's default lamp server ships with these off, so that won't be a problem unless your using some other system.

Anyway, hope that helps.  Granted the things that I have recommended are not secure.  It is VERY dangerous to grant your apache user passwordless sudo access, but its the only way that I can think of.

Cheers

---

### Post by Crdir on 2010-06-03
Thanks a lot, yeh you mentioned something I just had found

[http://exain.wordpress.com/2007/11/24/execute-system-commands-via-php/](http://exain.wordpress.com/2007/11/24/execute-system-commands-via-php/)

I ended giving www-data access to all functions with sudo. Since this is only a local test server with no important data this works for me.

thanks

---

