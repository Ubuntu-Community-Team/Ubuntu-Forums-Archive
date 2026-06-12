---
title: "Apache2 not working via hostname"
date: 2010-01-22
forum: General Help
---

### Post by Jibadee on 2010-01-22
Hello, 

My intranet page has stopped allowing users access via the hostname, if we connected using the IP the page loads up perfectly.

Via Hostname [http://intranet](http://intranet)

	The website declined to show this webpage
	 HTTP 403 
  	Most likely causes:
•	This website requires you to log in. 
  	What you can try:

  		Go back to the previous page.

  		More information

This error (HTTP 403 Forbidden) means that Internet Explorer was able to connect to the website, but it does not have permission to view the webpage.
For more information about HTTP errors, see Help.


C:\>nslookup intranet

Name:    intranet.home.co.uk
Address:  172.26.0.42

C:\>ping intranet

Pinging intranet.home.co.uk [172.26.0.42] with 32 bytes of data:
Reply from 172.26.0.42: bytes=32 time<1ms TTL=64
Reply from 172.26.0.42: bytes=32 time<1ms TTL=64
Reply from 172.26.0.42: bytes=32 time<1ms TTL=64

Ping statistics for 172.26.0.42:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms



Nothing serious showing in apache log.

cat /var/log/apache2/*.log

[Fri Jan 22 10:27:30 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 172.26.0.42 for ServerName
[Fri Jan 22 10:27:31 2010] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch configured -- resuming normal operations
[Fri Jan 22 10:28:06 2010] [notice] caught SIGWINCH, shutting down gracefully
[Fri Jan 22 10:31:17 2010] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch configured -- resuming normal operations
[Fri Jan 22 10:31:19 2010] [error] [client 172.26.0.101] File does not exist: /var/www/favicon.ico
[Fri Jan 22 10:31:25 2010] [error] [client 172.26.0.101] File does not exist: /var/www/favicon.ico
[Fri Jan 22 10:31:25 2010] [error] [client 172.26.0.101] File does not exist: /var/www/favicon.ico
[Fri Jan 22 10:32:16 2010] [error] [client 172.26.0.101] File does not exist: /var/www/favicon.ico
[Fri Jan 22 10:32:16 2010] [error] [client 172.26.0.101] File does not exist: /var/www/favicon.ico
[Fri Jan 22 10:48:15 2010] [error] [client 172.26.0.18] File does not exist: /var/www/favicon.ico


/var/log$ tail -F auth.log

Jan 22 10:51:00 intranet sudo: jibadee : TTY=pts/0 ; PWD=/var/log ; USER=root ; COMMAND=/bin/netstat -ntlp
Jan 22 10:51:00 intranet sudo: pam_unix(sudo:session): session opened for user root by jibadee(uid=0)
Jan 22 10:51:00 intranet sudo: pam_unix(sudo:session): session closed for user root
Jan 22 10:51:01 intranet CRON[7971]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Jan 22 10:51:01 intranet CRON[7971]: pam_unix(cron:session): session closed for user www-data
Jan 22 10:51:07 intranet sudo: jibadee : TTY=pts/0 ; PWD=/home/ajohnston ; USER=root ; COMMAND=/bin/netstat -ntlp
Jan 22 10:51:07 intranet sudo: pam_unix(sudo:session): session opened for user root by jibadee(uid=0)
Jan 22 10:51:07 intranet sudo: pam_unix(sudo:session): session closed for user root
Jan 22 11:01:01 intranet CRON[7982]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Jan 22 11:01:01 intranet CRON[7982]: pam_unix(cron:session): session closed for user www-data


Anyone point me in the right direction? :KS

---

### Post by Jibadee on 2010-01-22
I have just chmoded the www dir with 777 and now the front page is working but no links seem to be working 

ie 

[http://intranet/jibadee/?id=12](http://intranet/jibadee/?id=12) does not work

but 

[http://172.26.0.42/jibadee/?id=12](http://172.26.0.42/jibadee/?id=12) works

---

