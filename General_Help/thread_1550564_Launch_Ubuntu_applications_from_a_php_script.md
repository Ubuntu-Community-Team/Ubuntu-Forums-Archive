---
title: "Launch Ubuntu applications from a php script"
date: 2010-08-11
forum: General Help
---

### Post by MorleyPotter on 2010-08-11
Hi Everyone, I REALLY need some help please before I go mad, and apologies in advance if this shouldn't be here.

As  the subject of this post suggests i'm trying to launch Ubuntu  applications from a php script, i have tried different ways of doing  this but without much success.

Firstly i would like to explain why and maybe somebody may have a better suggestion or an alternative route...

I  am making a 'personal' remix of Ubuntu which will be a live CD i can  use for my university work (studying computer forensics), it will  basically be a minimal install with every Linux based forensics  application i can lay my hands on, instead of having a huge list of  shortcut's in the menu's that ship with Ubuntu I though it would be  fun/a challenge to make a fancy PHP based web site which contained a  database of the programs so i could search through them and find what i  need by category ect and then launch those applications from the same  site.

I can 'talk' to Ubuntu through some small scripts i've tried but i can't launch any applications.

Here is what i've got so far....

Code:
[COLOR=#000000][COLOR=#0000bb]<?php
[/COLOR][COLOR=#007700]echo [/COLOR][COLOR=#dd0000]"test1"[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#0000bb]$launcher [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]shell_exec[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]'ls'[/COLOR][COLOR=#007700]); 
print [/COLOR][COLOR=#dd0000]"<pre>[/COLOR][COLOR=#0000bb]$launcher[/COLOR][COLOR=#dd0000]</pre>"[/COLOR][COLOR=#007700];  

echo [/COLOR][COLOR=#dd0000]"test2"[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#0000bb]$output [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]exec[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]ls[/COLOR][COLOR=#007700]);
[/COLOR][COLOR=#0000bb]$doit2 [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]exec[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$output[/COLOR][COLOR=#007700]);
print [/COLOR][COLOR=#dd0000]"<pre>[/COLOR][COLOR=#0000bb]$doit2[/COLOR][COLOR=#dd0000]</pre>"[/COLOR][COLOR=#007700];

echo [/COLOR][COLOR=#dd0000]"test3"[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#0000bb]$cmd [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#dd0000]'ls'[/COLOR][COLOR=#007700];
echo [/COLOR][COLOR=#dd0000]"<pre>"[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]shell_exec[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$cmd[/COLOR][COLOR=#007700]).[/COLOR][COLOR=#dd0000]"</pre>"[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#0000bb]?>[/COLOR][/COLOR]
Which outputs....

test1

index.php
webalizer

test2

Webalizer V2.01-10 (Linux 2.6.32-24-generic) locale: C

test3

index.php
webalizer

Sucess i thought, so i then tried using the same formats to launch nautilus as a test, all of the below produced no results...

Code:
[COLOR=#000000][COLOR=#0000bb]<?php
[/COLOR][COLOR=#007700]echo [/COLOR][COLOR=#dd0000]"test1"[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#0000bb]$launcher [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]shell_exec[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]'/usr/bin/nautilus'[/COLOR][COLOR=#007700]); 
print [/COLOR][COLOR=#dd0000]"<pre>[/COLOR][COLOR=#0000bb]$launcher[/COLOR][COLOR=#dd0000]</pre>"[/COLOR][COLOR=#007700];  

echo [/COLOR][COLOR=#dd0000]"test2"[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#0000bb]$output [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]exec[/COLOR][COLOR=#007700](/[/COLOR][COLOR=#0000bb]usr[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]bin[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]nautilus[/COLOR][COLOR=#007700]);
[/COLOR][COLOR=#0000bb]$doit2 [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]exec[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$output[/COLOR][COLOR=#007700]);
print [/COLOR][COLOR=#dd0000]"<pre>[/COLOR][COLOR=#0000bb]$doit2[/COLOR][COLOR=#dd0000]</pre>"[/COLOR][COLOR=#007700];

echo [/COLOR][COLOR=#dd0000]"test3"[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#0000bb]$cmd [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#dd0000]'/usr/bin/nautilus'[/COLOR][COLOR=#007700];
echo [/COLOR][COLOR=#dd0000]"<pre>"[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]shell_exec[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]$cmd[/COLOR][COLOR=#007700]).[/COLOR][COLOR=#dd0000]"</pre>"[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#0000bb]?>[/COLOR][/COLOR]
Can anybody please help me out, i've searched all over the php forums, php.net and googled endlessly.

Any advice would be greatly appreciated

Many thanks,

MorleyPotter

---

### Post by mprokolo on 2010-08-11
Every command executed is ported back to "php" 
"Php" hasn't got a window manager so when you try to execute nautilus wich needs a display fails 
I can't tell you for sure if what you try is possible or not but it will be hard to do

---

### Post by MorleyPotter on 2010-08-11
Hi mprokolo, Thanks for your response, I have asked in the phpfreaks forums and they seem to think it is possible theoretically but very difficult, i'm thinking now of writing bash scripts for individual applications and getting php to launch them - does anyone in here know if that is possible, or even what the bash script should look like?

I'd have thought like this.....

#!/bin/bash
echo "Hi $USER launching...."
firefox

Thanks again.

EDIT: I've found out by running Apache as the current user it may be possible to launch applications directly, i'll keep you updated.

---

### Post by MorleyPotter on 2010-08-11
UPDATE: you  need to edit the /etc/apache2/envvars file to change the user &  group Apache runs as. You'll then need to restart Apache.
> 
sudo /etc/init.d/apache2 restart
							 						 						 							 							
 							 								

---

### Post by MorleyPotter on 2010-08-11
Just another update, here is where i am with my code (which unfortunately doesn't work) if you can spot any errors then please give me a shout...

```
<?php
echo "Firefox Launch Test";
echo "</br>";
$output = exec('firefox');
echo "<pre>$output</pre>"; //show any messages.
if ($output === "0")
{
echo "working....";
}
else {
echo "Firefox Launch Test Failed!";
}
echo "</br>";
echo "whoami query = ";
echo (`whoami`); //check Apache is loaded as current user.
?>
```And the result..... 

> Firefox Launch Test
Firefox Launch Test Failed!
whoami query = dave 

---

### Post by mprokolo on 2010-08-11
just a thought...maybe you are missing someting like 
```
export DISPLAY
```
used in ssh for X11 forwarding

another thought is to try it like this
```
xterm -e firefox
``` 
which opens an xterminal and executes "firefox" command

---

### Post by MorleyPotter on 2010-08-12
Yeah thanks [mprokolo]("http://ubuntuforums.org/member.php?u=344267") i've been reading the manual on exec() on php.net [here]("http://php.net/manual/en/function.exec.php"), and i think it does need some extra parameters but i'm not sure what, i'm currently trying different things but nothing yet i'll keep this post updated if i find out how

---

### Post by MorleyPotter on 2010-08-12
I've made a small amount of progress but i was wondering if anyone could 'tweak' this code to get it to work.

1st the code then the output.

[PHP]<?php
exec('TERM=xterm display localhost:0.0 /usr/bin/firefox n 1 b i', $xterm, $error );
echo nl2br(implode("\n",$xterm));
if ($error){
    exec('TERM=xterm display localhost:0.0 /usr/bin/firefox n 1 b 2>&1', $error );
    echo "Error: ";
    exit($error[0]);
}
?>[/PHP]> Error: display: unable to open X server `' @ display.c/DisplayImageCommand/422.

I tried adding 'startx' in various places but it just makes the page hang?

---

### Post by mprokolo on 2010-08-12
startx is used in order to start the whole environment which is started

just forget about the display for a moment if you pass the command like this
```

xterm -e /usr/bin/firefox
or
xterm -e /usr/bin/firefox&

```
 what happens?

Also have a look at the last post there:
[http://ubuntuforums.org/archive/index.php/t-1040260.html](http://ubuntuforums.org/archive/index.php/t-1040260.html)
maybe it has something to do with x11 security
(I know it is for ssh but in theory you are trying to do the same launch a gui program from command prompt)

also do an 
```
echo $DISPLAY
```
using php

---

### Post by MorleyPotter on 2010-08-14
> **mprokolo said:**
> startx is used in order to start the whole environment which is started
 
just forget about the display for a moment if you pass the command like this
```

xterm -e /usr/bin/firefox
or
xterm -e /usr/bin/firefox&

```
what happens?
 
 
Both produce a blank screen?
 
 > 
also do an 
```
echo $DISPLAY
```
using php
 
 
And this produces no results??
 
I've had a look at that thread and i think that ssh may be a possibilty, the only thing is the applications are to be opened on the server so i'm not sure how or even if it possible to use ssh to connect from php (being server side) to the local machine?

---

