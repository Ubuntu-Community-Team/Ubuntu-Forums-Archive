---
title: "Codeigniter on Ubuntu 10"
date: 2011-02-21
forum: General Help
---

### Post by ftom2 on 2011-02-21
Hi,
  I’ve got Codeigniter on Ubuntu 10 (LAMP). I have an htaccess file:


  [COLOR=#000000] [COLOR=#007700]<[/COLOR][COLOR=#0000bb]IfModule mod_rewrite[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]c[/COLOR][COLOR=#007700]>
[/COLOR][COLOR=#0000bb]RewriteEngine On
RewriteBase [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]dort
[/COLOR][COLOR=#ff8000]#Removes access to the system folder by users.
#Additionally this will allow you to create a System.php
#controller, previously this would not have been possible.
#'system' can be replaced if you have renamed your system folder.
[/COLOR][COLOR=#0000bb]RewriteCond [/COLOR][COLOR=#007700]%[/COLOR][COLOR=#0000bb]{REQUEST_URI} [/COLOR][COLOR=#007700]^[/COLOR][COLOR=#0000bb]system[/COLOR][COLOR=#007700].*
[/COLOR][COLOR=#0000bb]RewriteRule [/COLOR][COLOR=#007700]^(.*)$ /[/COLOR][COLOR=#0000bb]dort[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]index[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]php[/COLOR][COLOR=#007700]?/$[/COLOR][COLOR=#0000bb]1 [L]
[/COLOR][COLOR=#ff8000]#Checks to see if the user is attempting to access a valid file,
#such as an image or css document, if this isn't true it sends
#the request to index.php
[/COLOR][COLOR=#0000bb]RewriteCond [/COLOR][COLOR=#007700]%[/COLOR][COLOR=#0000bb]{REQUEST_FILENAME} [/COLOR][COLOR=#007700]!-[/COLOR][COLOR=#0000bb]f
RewriteCond [/COLOR][COLOR=#007700]%[/COLOR][COLOR=#0000bb]{REQUEST_FILENAME} [/COLOR][COLOR=#007700]!-[/COLOR][COLOR=#0000bb]d
RewriteRule [/COLOR][COLOR=#007700]^(.*)$ /[/COLOR][COLOR=#0000bb]dort[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]index[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]php[/COLOR][COLOR=#007700]?/$[/COLOR][COLOR=#0000bb]1 [L]
[/COLOR][COLOR=#007700]</[/COLOR][COLOR=#0000bb]IfModule[/COLOR][COLOR=#007700]>
<[/COLOR][COLOR=#0000bb]IfModule [/COLOR][COLOR=#007700]![/COLOR][COLOR=#0000bb]mod_rewrite[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]c[/COLOR][COLOR=#007700]>
[/COLOR][COLOR=#ff8000]# If we don't have mod_rewrite installed, all 404's
# can be sent to index.php, and everything works as normal.
# Submitted by: ElliotHaughin
[/COLOR][COLOR=#0000bb]ErrorDocument 404 [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]index[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]php
[/COLOR][COLOR=#007700]</[/COLOR][COLOR=#0000bb]IfModule[/COLOR][COLOR=#007700]> 

[/COLOR] [/COLOR] 
  Up until now, we connected the remote server with IP and everything  worked fine, now, a virtual host was defined for the server and suddenly  nothing works except for the login page (index.php). I’ve changed  $config[‘base_url’] in config.php but i keep getting 404.
  Please help :(

---

### Post by veggen on 2011-02-21
You'll probably have more luck on CodeIgniter forum...

---

