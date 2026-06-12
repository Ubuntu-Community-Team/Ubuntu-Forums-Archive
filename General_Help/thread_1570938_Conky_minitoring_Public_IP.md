---
title: "Conky: minitoring Public IP"
date: 2010-09-08
forum: General Help
---

### Post by robbiemacg on 2010-09-08
Is there anyway I can prepare a script that will execute when a new connection is made? I want to get Conky to check/print my Public IP whenever a new connection is made... and then continue checking at a specified interval.

My Conky is set to run at start up (more accurately 10 seconds after log in).
I have not generally connected to any network by the time my Conky is running, so the script that provides information about my Public IP doesn't return any information for Conky to print (at least, not for 15 minutes).

As things stand, I might alter my conkyStart script:
```
#!/bin/bash
sleep 10 && conky ;
```... say, give myself 30 seconds (instead of the current 10) to connect to a network before starting up the old Conky.

or

I could change the interval at which Conky checks my Public IP
```
${execi 900 ~/.conkycolors/bin/conkyIp}
```... maybe get it to check in every 5 minutes or so.

But I don't really want to do either of those things if I don't have to.

I want to prepare a script that will execute when a new connection is made, then I want my Conky to run the above operation at the specified interval.

Any thoughts? has anyone tried to accomplish something similar?

*Background: I run Ubuntu on a laptop, and often use my machine at meeting in hotels, cafes, etc. Sometimes, I'll shut the lid, change locations, get right back to work. I would like to be able to tell accurately, at a glance, what my Public IP is.

---

### Post by bodhi.zazen on 2010-09-08
```
curl ifconfig.me
```

Returns your public IP

Hope that helps some way ;)

---

### Post by robbiemacg on 2010-09-09
Cool. So, by pairing the **curl** command with the server address provided I can return my Public IP. I can skip a step, avoid running a script or chaining commands.   

If I understand correctly, the idea is that this method's a little more direct, requires fewer resources? I'm not running a script, **wget**ing, **grep**ing or anything like that... 
so, maybe I can safely run the operation that returns my Public IP more frequently?

Am I correctly understanding the thrust of [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")'s advice?

---

### Post by bodhi.zazen on 2010-09-09
I was suggesting an easy way to obtain your public IP in a single (simple) command.

What to do from there is up to you. I see no reason to run that command with much regularity, how often do your anticipate your public ip to change ? You could run it at log in and manually if (as) needed.

---

### Post by robbiemacg on 2010-09-10
Thanks for you help.
I've read the **curl** man page and visited [http://ifconfig.me](http://ifconfig.me). I feel like you've introduced me to some simple, useful new tools.

---

### Post by t0p on 2010-09-10
If you check out [this forum thread]("http://ubuntuforums.org/archive/index.php/t-1284459.html"), you will see how I achieved something similar.  Well, with a little help from my friends...

---

### Post by stinkeye on 2010-09-10
You could use a script.Save as **conkyip** and make executable.
```
#!/bin/bash

sleep 3 && curl --retry 4 "ifconfig.me"
```

and then use the **if_up** variable in your conky
eg
```
${if_up [COLOR="DarkOrange"]eth0[/COLOR]}${execi 900 [COLOR="Magenta"]/home/glen/conky/conkyip[/COLOR]}${else}No Network...${endif}
```
[COLOR="#ff8c00"]Change for your interface[/COLOR]
[COLOR="#ff00ff"]change for path to your script[/COLOR]

Won't change if your ip changes but will give you an ip at startup.

---

### Post by robbiemacg on 2010-09-10
Many thanks!
I'm still doing some experimenting, but I feel that the tips, tools, and information shared by [t0p]("http://ubuntuforums.org/member.php?u=380385") and [stinkeye]("http://ubuntuforums.org/member.php?u=684510") have helped me achieve the kind of functionality I was after.

I'm marking this thread **solved**. 
With the help of forum members I've learned a simple new command that'll return my Public IP; I've figured out how to build/run a script that will check periodically to see if my network has changed; I can trigger/delay the operation that returns my IP so that it displays when I want it to (after login and when I open the lid after suspending).

Thanks very much, [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054"), [t0p]("http://ubuntuforums.org/member.php?u=380385") and [stinkeye]("http://ubuntuforums.org/member.php?u=684510")

---

### Post by knezmej on 2013-01-14
thank You :)

---

