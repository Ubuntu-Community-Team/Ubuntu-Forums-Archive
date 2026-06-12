---
title: "Synergy script problem... or ?"
date: 2011-06-19
forum: General Help
---

### Post by meanmrmustard on 2011-06-19
Hopefully I've explained things clearly and haven't left out anything relevant.

I installed Synergy (the client on the Windows XP laptop and the server on Ubuntu 10.04) following the tutorial at [http://synergy2.sourceforge.net/configuration.html](http://synergy2.sourceforge.net/configuration.html).

I have them configured and running properly.

I then booted into the Maverick installation on the (dual boot) laptop and installed another client, following instructions at the same page then went to the /autostart.html page to set up autostart.

Attempting to start the client manually with, $ /Library/StartupItems/SynergClient/SynergyClient - after a couple minor changes listed just below, 
I got this error:


 ```
.: 2: Can't open /etc/rc.common
```

As root it's the same.
For the record, I got the same error before the changes were made.

Searching on that error I found [http://www.mackb.com/Uwe/Forum.aspx/mac/20491/Running-a-command-in-Terminal](http://www.mackb.com/Uwe/Forum.aspx/mac/20491/Running-a-command-in-Terminal)

The suggested file structure there is:
/Library/
    StartupItems/
         SynergyClient/
              StartupParameters.plist
              SynergyClient


I made these changes, Sourceforge tutorial had the script file and it's directory both named "Synergy" instead of "SynergyClient".
 
The mackb file:
[http://pastebin.com/32U3DSCz](http://pastebin.com/32U3DSCz)
My File:
[http://pastebin.com/Z1LDWJwQ](http://pastebin.com/Z1LDWJwQ)

Other parameters were in that post (the mackb file) but I was unsure they were necessary so left them out so as to not confuse things further.

Further down the page it says:
```
Make sure these files and folders have the correct owner/group and
permissions:

cd /Library/StartupItems
sudo chmod -R SynergyClient root:wheel
sudo chmod -R 755 SynergyClient
sudo chmod 644 SynergyClient/StartupParameters.plist
```

The first command returns
chmod: invalid mode: `SynergyClient'


Maybe that command should have been "chgrp" instead of "chmod", since we're not talking about permissions?

Looking at the groups through the GUI I see no "wheel" group, which may be a problem?

The second command returns no error nor does the third.

I guess that autostart wouldn't be interfering at this point but I'll include the StartupParameters.plist file also in case it's borked too.
```
{ 
              Description = "Synergy Client"; 
              Provides = ("Synergy"); 
              Requires = ("Network"); 
              OrderPreference = "None"; 
} 
```


Maybe "SynergyClient" should be the actual name of the machine?... and "Network" should be the IP address... of the server?... or client?

I used the names rather than IP addresses in setting up the server and Windows client and it worked, so I figured, "Let sleeping dogs lie".

The files were cut and pasted, except for substitutions to reference my machines.

I have very little experience with bash scripts and am not sure how to troubleshoot it.

Maybe I'm missing something obvious.

Any input would be greatly appreciated.

Thanks for reading!

Mr.M

---

