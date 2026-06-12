---
title: "FTP parameters"
date: 2010-05-07
forum: General Help
---

### Post by TorMike on 2010-05-07
[SIZE=2]I'd want to use ubuntu as [/SIZE]test server for a website I'm writing.  It's the usual stuff, HTML on website, PHP source code and access via Apache server.

To use PHP ftp protocol I need to connect to a ftp server.

I've install vsftp on my 9.10 server (requiring Authenticate FTP ie: local_enable=YES and write_enable=YES in vsftpd.init file).

Here's the standard set of argument required for PHP ftp:

[PHP]  
  $ftp_user_name='xx';
  $ftp_user_pass='xxx';
  $ftp_server='kelowna';  // --> This the name of my ubuntu server
  $ftp_dir='/var/www/picfrisky/uploads/';
  
  // connect, login, and transfer the file
  $conn = ftp_connect($ftp_server);
  $login_result = ftp_login($conn, $ftp_user_name, $ftp_user_pass);
[/PHP]My question is:  What to use as a username & password?  My server logon?

It's a simple question but I'm really stuck.

---

### Post by _0R10N on 2010-05-07
You have to create ftp accounts
[http://www.faqs.org/docs/securing/chap29sec295.html](http://www.faqs.org/docs/securing/chap29sec295.html)
There's a short guide relating to this subject.

---

