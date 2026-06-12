---
title: "php file work in CLI not in Browser"
date: 2010-03-05
forum: General Help
---

### Post by mraza08 on 2010-03-05
Hi, I need help please, i have installed mtn and its work perfectly in shell, i have written a php script to run mtn in browser, if i run this php script in CLI it works well and if i run in browser its not working, please any help.. here is the code for php

```
[COLOR=#000000][COLOR=#0000bb]<?php
error_reporting[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]E[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]ALL[/COLOR][COLOR=#007700]);

if ([/COLOR][COLOR=#0000bb]function_exists[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]shell_exec[/COLOR][COLOR=#007700])) {
echo [/COLOR][COLOR=#dd0000]"Shell Function is Available<br />"[/COLOR][COLOR=#007700];
}

[/COLOR][COLOR=#0000bb]$output [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]shell_exec[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]'./mtn'[/COLOR][COLOR=#007700]);
if([/COLOR][COLOR=#0000bb]$output[/COLOR][COLOR=#007700]) {
echo [/COLOR][COLOR=#dd0000]"<pre>[/COLOR][COLOR=#0000bb]$output[/COLOR][COLOR=#dd0000]</pre>"[/COLOR][COLOR=#007700];
}else{
echo [/COLOR][COLOR=#dd0000]"Not worked and returned: " [/COLOR][COLOR=#007700]. [/COLOR][COLOR=#0000bb]print_r[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$output[/COLOR][COLOR=#007700]);
}
[/COLOR][COLOR=#0000bb]?>[/COLOR][/COLOR]
```and result in browser i get is
> 
Shell Function is Available
Not worked and returned: 1please help me to solve it, i am using ubuntu 8.10 server thanks

please note all other php are working good, only this mtn function is problem. 
[https://sourceforge.net/projects/moviethumbnail/](https://sourceforge.net/projects/moviethumbnail/)

---

### Post by BbUiDgZ on 2010-03-05
> **mraza08 said:**
> Hi, I need help please, i have installed mtn and its work perfectly in shell, i have written a php script to run mtn in browser, if i run this php script in CLI it works well and if i run in browser its not working, please any help.. here is the code for php

```
[COLOR=#000000][COLOR=#0000bb]<?php
error_reporting[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]E[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]ALL[/COLOR][COLOR=#007700]);

if ([/COLOR][COLOR=#0000bb]function_exists[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]shell_exec[/COLOR][COLOR=#007700])) {
echo [/COLOR][COLOR=#dd0000]"Shell Function is Available<br />"[/COLOR][COLOR=#007700];
}

[/COLOR][COLOR=#0000bb]$output [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]shell_exec[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]'./mtn'[/COLOR][COLOR=#007700]);
if([/COLOR][COLOR=#0000bb]$output[/COLOR][COLOR=#007700]) {
echo [/COLOR][COLOR=#dd0000]"<pre>[/COLOR][COLOR=#0000bb]$output[/COLOR][COLOR=#dd0000]</pre>"[/COLOR][COLOR=#007700];
}else{
echo [/COLOR][COLOR=#dd0000]"Not worked and returned: " [/COLOR][COLOR=#007700]. [/COLOR][COLOR=#0000bb]print_r[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$output[/COLOR][COLOR=#007700]);
}
[/COLOR][COLOR=#0000bb]?>[/COLOR][/COLOR]
```and result in browser i get is
please help me to solve it, i am using ubuntu 8.10 server thanks

please note all other php are working good, only this mtn function is problem. 
[https://sourceforge.net/projects/moviethumbnail/](https://sourceforge.net/projects/moviethumbnail/)

whats the apache error logs saying?

---

