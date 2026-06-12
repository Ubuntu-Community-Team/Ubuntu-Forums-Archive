---
title: "Easier apcupsd-cgi url?"
date: 2009-06-26
forum: General Help
---

### Post by crimsondr on 2009-06-26
Hi all,

I installed a UPS recently with apcupsd.  I also setup the web site monitoring.  However, the default url is quite cumbersom ([http://localhost/cgi-bin/apcupsd/multimon.cgi](http://localhost/cgi-bin/apcupsd/multimon.cgi)).

How can I make a nicer url redirect to this?  Ie.  [http://localhost/apcups](http://localhost/apcups) would redirect to [http://localhost/cgi-bin/apcupsd/multimon.cgi](http://localhost/cgi-bin/apcupsd/multimon.cgi)

Thanks.

---

### Post by tjhart85 on 2010-06-15
I know this is oldish, but I was looking for the same thing & couldn't find it.

I wound up hacking together a PHP redirect that would work for either internal network use or exteral.

Change SERVERNAME to be the hostname/ip for the machine that the ups is on.
Change EXTERNAL_NO-IP_ADDRESS to your external IP address that is also port 80 forwarded to the machine.  I use a no-ip address.

Just save the file to:
SERVERNAME/apcups.php
in your case and it should work

Works great for me with information I pieced together from around the PHP beginners pages.


[PHP]<?php

$pos = strrpos($_SERVER['REMOTE_ADDR'], "192.168.");	//Will only be 192.168. if accessing from local network.
if ($pos !== false) { 
	header( 'Location: http://SERVERNAME/cgi-bin/apcupsd/multimon.cgi' ) ;
} else {
	header( 'Location: http://EXTERNAL_NO-IP_ADDRESS/cgi-bin/apcupsd/multimon.cgi' ) ;
}
?>
[/PHP]

---

