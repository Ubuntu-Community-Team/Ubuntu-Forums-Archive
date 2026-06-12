---
title: "500 internal server error"
date: 2011-07-28
forum: General Help
---

### Post by itba on 2011-07-28
hi,
I copied my printenv.pl file into /usr/lib/cgi-bin
ran
```

chmod +rx printenv.pl

```in my apache2.conf file, I added the following lines
```


<Files ~ "\.pl$">
Options +ExecCGI
</Files>
AddHandler cgi-script .pl


```restarted the apache server
```

/etc/init.d/apache2 start

```but when I go to 
[html]
http://localhost/cgi-bin/printenv.pl
[/html]I get the following error:
```

**Internal Server Error**

 The server encountered an internal error or misconfiguration and was unable to complete your request.
 Please contact the server administrator,  webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.
 More information about this error may be available in the server error log.
  Apache/2.2.17 (Ubuntu) Server at localhost Port 80
```here's my error log file:
```

[Thu Jul 28 19:28:43 2011] [error] [client 127.0.0.1] (2)No such file or directory: exec of '/usr/lib/cgi-bin/printenv.pl' failed
[Thu Jul 28 19:28:43 2011] [error] [client 127.0.0.1] Premature end of script headers: printenv.pl

```but this is what my /usr/lib.cgi-bin directory looks like
```

:/usr/lib/cgi-bin$ ls -l
total 8
-rwxr-xr-x 1 root root 331 2011-07-28 19:01 printenv.pl
-rwxr-xr-x 1 root root 335 2011-07-28 18:50 printenv.pl~

```can you please help me fix this...thanks!

---

### Post by itba on 2011-07-31
Nobody knows?

---

