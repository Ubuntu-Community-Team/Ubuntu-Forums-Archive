---
title: "mediawiki restrict upload permissions"
date: 2010-01-14
forum: General Help
---

### Post by Johannekie on 2010-01-14
Hi,
 
I'm having some trouble restricting uploads from usergroups.
 
I tried the following in the LocalSettings.php file:
 
$wgGroupPermissions['*']['upload'] = false;
$wgGroupPermissions['something']['upload'] = false;
 
But even if I login with a user from usergroup "something", I'm allowed to upload files.
 
What am I doing wrong? :(

---

### Post by Johannekie on 2010-01-18
I found the solution.
 
You have to do:
 
[COLOR=#000088]$wgGroupPermissions[/COLOR][COLOR=#009900][[/COLOR][COLOR=#0000ff]'user'[/COLOR][COLOR=#009900]][[/COLOR][COLOR=#0000ff]'upload'[/COLOR][COLOR=#009900]][/COLOR] [COLOR=#339933]=[/COLOR] **[COLOR=#009900]false[/COLOR]**[COLOR=#339933];[/COLOR]

first, and restrict per user group. E.G:
 
[COLOR=#000088]$wgGroupPermissions[/COLOR][COLOR=#009900][[/COLOR][COLOR=#0000ff]'user'[/COLOR][COLOR=#009900]][[/COLOR][COLOR=#0000ff]'upload'[/COLOR][COLOR=#009900]][/COLOR] [COLOR=#339933]=[/COLOR] **[COLOR=#009900]false[/COLOR]**[COLOR=#339933];[/COLOR]
[COLOR=#000088]$wgGroupPermissions[/COLOR][COLOR=#009900][[/COLOR][COLOR=#0000ff]'something'[/COLOR][COLOR=#009900]][[/COLOR][COLOR=#0000ff]'upload'[/COLOR][COLOR=#009900]][/COLOR] [COLOR=#339933]=[/COLOR] **[COLOR=#009900]false[/COLOR]**[COLOR=#339933];[/COLOR]
[COLOR=#000088]$wgGroupPermissions[/COLOR][COLOR=#009900][[/COLOR][COLOR=#0000ff]'sysop'[/COLOR][COLOR=#009900]][[/COLOR][COLOR=#0000ff]'upload'[/COLOR][COLOR=#009900]][/COLOR] [COLOR=#339933]=[/COLOR] **[COLOR=#009900]true[/COLOR]**[COLOR=#339933];[/COLOR]

---

