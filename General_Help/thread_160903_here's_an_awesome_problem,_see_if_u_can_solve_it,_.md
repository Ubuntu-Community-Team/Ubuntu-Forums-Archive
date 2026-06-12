---
title: "here's an awesome problem, see if u can solve it, haha."
date: 2006-04-15
forum: General Help
---

### Post by f0rgiv3n on 2006-04-15
alright, so, check this out. 
my first stage - i had xp pro on my machine and used it for gaming etc... 
second stage - i loaded fedora core 4 ran great, DNS on it works great, gets it dynamically but when i try to connect ot the internet it finds the website but when "connecting..." it times out. What in the heck!?! so, i though it was a fedora driver problem
third stage, i load on ubuntu hoping it would default to maybe a different driver. Same exact problem!!!!!!!!!!!!!!!!!!! what in the heck?! i can resolve FQDN's, no problem but my connections always time out, on my xp machines connected to the same router they work great! what is it?! PLEASE HELP ME! I'M GOING CRAZY! HAHA.](*,) ](*,) ](*,)

---

### Post by trent dillman on 2006-04-15
Are the timeouts solely in a browser (like Firefox) or are they on other connections as well? Does apt-get work? Can you browse with lynx/mozilla/epiphany/dillo?

---

### Post by az on 2006-04-15
Are you using wireless?  What are the details of your insternet connection?

---

### Post by f0rgiv3n on 2006-04-15
well, first of all it's only seemingly with the browser, and i'm connected to a switch, and then to the dsl modem. just a little 5 port switch. i'm thinking it's just the browser tho. and how do i browse with that lynx thing?

---

### Post by trent dillman on 2006-04-15
open a terminal and see if

```
sudo apt-get update
``` connects.

And for lynx, just ```
sudo apt-get install lynx
```

Then you can browse with
```
lynx www.google.com
```

NOTE: lynx must be run in a terminal, as it is a command-line www browser!


EDIT: see [http://ubuntuforums.org/showthread.php?t=160886](http://ubuntuforums.org/showthread.php?t=160886) for lynx alternatives...

---

### Post by az on 2006-04-15
[QUOTE=f0rgiv3n]well, first of all it's only seemingly with the browser, and i'm connected to a switch, and then to the dsl modem. just a little 5 port switch. i'm thinking it's just the browser tho. and how do i browse with that lynx thing?[/QUOTE]
Disable ipv6.

Type 
about:config
in the firefox bar and scroll down to

network.dns.disableIPv6 

and change that to true.

---

### Post by f0rgiv3n on 2006-04-15
WoW! that is amazing you guys rock, i appreciate it so much, thank you again! i'm sure i'll be seein ya again on the forums ;) . thanks a lot guys, i did both of what you guys suggested, first i did lynx and it worked great, so, i figured it was the ipv6 so, i did wha tyou said with the about:config and disabled it and now it works great! why does ipv6 come default? thanks again!

---

### Post by az on 2006-04-16
[QUOTE=f0rgiv3n] why does ipv6 come default? thanks again![/QUOTE]

Because countries newly developing the internet will use that exclusively.

---

### Post by f0rgiv3n on 2006-04-16
oh wow, that's cool. I knew it! ;) i knew we were running out of ip addresses i didn't know they had fully implemented ipv6, that's cool :)

---

