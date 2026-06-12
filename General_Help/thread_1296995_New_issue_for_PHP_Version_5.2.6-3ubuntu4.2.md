---
title: "New issue for PHP Version 5.2.6-3ubuntu4.2 ?"
date: 2009-10-21
forum: General Help
---

### Post by yilin on 2009-10-21
I'm running ubuntu 9.04 upgraded from 8.10 on my d630 laptop as a developer box.

The apache2+php5 system is kind of working (phpmyadmin runs ok on it), but for the following script, it behaves quite differently than my win2003 server + php5.2.5 and redhat + php5.1:

[COLOR="Gray"]<?php
// ck.php
$ckVar = $_COOKIE['test'];
if(isset($ckVar)) {
  echo "cookieValue is ",$ckVar;
} else {
  echo "cookie is not set";
}
SetCookie('test','123',time()+12,'/');
?>[/COLOR]

The response of it to the request [http://localhost/ck.php](http://localhost/ck.php) is

[COLOR="Red"]cookie is not set
Warning: Cannot modify header information - headers already sent by (output started at /home/www/htdocs/ck.php:7) in /home/www/htdocs/ck.php on line 8[/COLOR]

and reload the page will not change the output.

While for my other systems, the same script will return a page saying 'cookieValue is 123' after a reloading. 

I know any setting to header should be done before content. But why my other systems can tolenrate this and automatically handle this correctly?

Could anyone help me understand how to fix my developer system? Or let me know where to find the solution? 

Thanks a lot.

The anorying thing is that my developer box breaks my ad image generating code in the same way!

---

### Post by yilin on 2009-10-21
Well, it's the php configuration problem. For some reason output_buffering is not turned on.

---

