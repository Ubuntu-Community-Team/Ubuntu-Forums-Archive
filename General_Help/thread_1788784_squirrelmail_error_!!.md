---
title: "squirrelmail error !!"
date: 2011-06-23
forum: General Help
---

### Post by samir_12 on 2011-06-23
hello 
i was trying to access my squirrelmail for the first time after install from :
 
 
[[COLOR=#22229c]http://10.191.11.110/squirrelmail/[/COLOR]]("http://10.191.11.110/squirrelmail/") or [[COLOR=#22229c]http://mail.mydomaine.com/squirrelmail[/COLOR]]("http://mail.mydomaine.com/squirrelmail")
 
 i got this error 


<?php

/**
* index.php
*
* Redirects to the login page.
*
* @copyright 1999-2010 The SquirrelMail Project Team
* @license [[COLOR=#22229c]http://opensource.org/licenses/gpl-license.php[/COLOR]]("http://opensource.org/licenses/gpl-license.php") GNU Public License
* @version $Id: index.php 13893 2010-01-25 02:47:41Z pdontthink $
* @package squirrelmail
*/

// Are we configured yet?
if( ! file_exists ( 'config/config.php' ) ) {
echo '<html><body><p><strong>ERROR:</strong> Config file ' .
'&quot;<tt>config/config.php</tt>&quot; not found. You need to ' .
'configure SquirrelMail before you can use it.</p></body></html>';
exit;
}

// If we are, go ahead to the login page.
header('Location: src/login.php');

?>
also got this 
[[COLOR=#22229c]http://10.191.11.110/squirrelmail/sr...test.[/COLOR]]("http://10.191.11.110/squirrelmail/sr...test.")
[COLOR=#22229c][/COLOR] 
[COLOR=#22229c]Forbidden[/COLOR]

You don't have permission to access /squirrelmail/src/configtest.php on this server.

Apache/2.2.16 (Ubuntu) Server at 10.191.11.110 Port 80

dont know what went wrong i followed the instruction bit by bit lol 

thanks in advance

---

