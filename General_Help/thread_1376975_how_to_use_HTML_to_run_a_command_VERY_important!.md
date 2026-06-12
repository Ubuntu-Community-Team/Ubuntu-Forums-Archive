---
title: "how to use HTML to run a command? VERY important!"
date: 2010-01-09
forum: General Help
---

### Post by gfunkera on 2010-01-09
ok it may involve more than html...

but how do i get a web page on my apache server to run a command... lets say "fortune" or "grep" or "ls" or (anything actually) by having someone visiting the website and pushing a submit button? would that be a php thing? or python? if this isnt clear please tell me and ill clarify what im trying to do..

---

### Post by NoaHall on 2010-01-09
You'd need to use a server side scripting language such as php. html is a mark-up language. It makes things look pretty, and that's it.

Anyway, shell_exec or exec() are the commands you want.

---

### Post by gfunkera on 2010-01-09
do u recommend any sites that i can use as referrence? are shell_exec and exec() php specific?

---

### Post by NoaHall on 2010-01-09
> **gfunkera said:**
> do u recommend any sites that i can use as referrence? are shell_exec and exec() php specific?

[http://www.php.net/manual/en/function.exec.php](http://www.php.net/manual/en/function.exec.php)

Use exec("ls") or whatever :)

---

### Post by gfunkera on 2010-01-09
okay im startin to get it... thanks.. im trying to figure out how to get the output to show up somewhere that i can see it... so if i run 'ls' with php, how can i get its output to be shown on the site?

---

### Post by NoaHall on 2010-01-09
> **gfunkera said:**
> okay im startin to get it... thanks.. im trying to figure out how to get the output to show up somewhere that i can see it... so if i run 'ls' with php, how can i get its output to be shown on the site?

You assign it to a variable.
For example:
```

<html>
<head>
</head>
<body>
<?php
$a=exec("ls");
echo $a;
?>
</body>
</html>

```

---

### Post by gfunkera on 2010-01-10
ok im havin trouble again with the exec() and shell_exec() commands..

they work but not the same way all the time... like for instance if i do 'ls' and assign to a variable then echo the variable, itll show the results of ls... but when i use 'fortune' i dont get anything outta that...

also i noticed that the exec() command only shows a handful of characters from the output but if i use shell_exec() it shows alot more...

i also cant figure out how to do a line break (for some odd reason) with the php.... im using "\n" but it doesnt produce a break in the output... thats a minor issue tho.. just wonderin if you got any ideas for it..

further more i noticed that some commands that require arguments or other information passed to them dont seem to work properly with these commands.. like if i do "fortune | cowthink"... theres absolutely no output!

im curious as to what/where the shell is thats running the commands off the web page... i would like to have the shell output in entirety... does that make sense?

---

### Post by dcstar on 2010-01-11
> **gfunkera said:**
> 
.........
i also cant figure out how to do a line break (for some odd reason) with the php.... im using "\n" but it doesnt produce a break in the output... thats a minor issue tho.. just wonderin if you got any ideas for it..
.........

Shell commands are designed to output data to be read off a terminal, an HTML web page is **not** a terminal.

You need to understand a lot more about Linux and HTML that can (or should) be taught in a general Linux support forum.

---

### Post by Warren Watts on 2010-01-11
Perl can also be used to accomplish the same task.  Here's an example that executes "uptime" on the server and returns the result as an HTML page.

```
#!/usr/bin/perl

######################################################################################
# show_uptime_sample.pl  1/11/10
# Author: Warren Watts (kingbeetle_66(at)yahoo(dot)com
# When called from a web page, this program will execute the uptime command
# and return the output as an HTML page.

# Copyright 2010 Warren B. Watts
# This work is made available under the terms of the
# Creative Commons Attribution-ShareAlike 3.0 license,
# http://creativecommons.org/licenses/by-sa/3.0/.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
#######################################################################################

use strict;
my   $uptime = `uptime`;
$uptime =~ s/ /&nbsp;/g;    # find and replace all spaces with HTML compliant spaces
$uptime =~ s/\n/<br>\n/g;  # find and replace all newlines with HTML breaks (<br >)

print "Content-type: text/html\n\n";
print <<End_of_Error;
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <title>Server Uptime</title>
</head>
<body>
End_of_Error
print "  <h2>Server Uptime</h2>\n";
print "  <div style=\"font-family:Courier;\">\n";
print $uptime;
print "</div></body></html>";

```

Calling the perl script from the browser will result in a page with HTML that looks something like this: 
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <title>Server Uptime</title>
</head>
<body>
  <h2>Server Uptime</h2>
  <div style="font-family:Courier;">
&nbsp;02:49:39&nbsp;up&nbsp;9&nbsp;days,&nbsp;&nbsp;6:00,&nbsp;&nbsp;1&nbsp;user,&nbsp;&nbsp;load&nbsp;average:&nbsp;0.01,&nbsp;0.05,&nbsp;0.01<br>

</div></body></html>
```

Do keep in mind that DANGEROUS THINGS CAN HAPPEN if you accept input (say, on a form) and allow that input to be passed to your served-side program and executed.  

This is true regardless of the language used server-side.

---

