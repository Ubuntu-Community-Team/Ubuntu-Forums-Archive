---
title: "AutoExpungeInEvolution"
date: 2011-02-03
forum: General Help
---

### Post by kaspar_silas on 2011-02-03
Does anyone know how to make evolution automatically expunge.

Currently to delete my emails from the server I have to select the account, right-click on "Deleted Items" and select "Empty deleted items". This works a treat but necessitates me sitting at a screen clicking. 

I know evolution can do this automatically on evolution shutdown. However shutting down evolution and reopening it every 5 minutes is not exactly elegant. Plus when evolution reopens it will pop up in the current workspace over whatever you are currently doing.

Hence the plan is to add a cronjob or even run this script in background:

```
#!/bin/bash
while true;
do 
	[Equivalent command to right-clicking "Empty deleted items"]	
	sleep 120; 
done
```

So does anyone have any idea what this equivalent command is.
Thanks for any help.

---

### Post by kaspar_silas on 2011-02-09
Alternatively does anyone have any other ideas how to do this?

---

### Post by kaspar_silas on 2011-03-01
Well I figured it out myself. Hence my monologue continues with the solution to the previously outlined problem. The solution is this script which I run in the background:

```

#!/bin/bash
while true;
do 
    expect << EOF
    set timeout 10
    spawn telnet [MY.IMAP.SERVER] imap
    expect "Server Ready"
    send "0 login [EMAIL-NAME] [EMAIL-PASSWORD]\r"
    expect "LOGIN completed"
    send "0 select inbox\r"
    expect "SELECT completed"
    send "0 expunge\r"
    expect "EXPUNGE completed"
    send "0 logout\r"
    exit
    EOF	
    sleep 300; 
done
```

Obviously you need to install expect and change the [ ] parts to your own account setting. 

I have no idea how to extend it to work with SSL or TLS. If anyone does maybe a little nod in the right direction would be nice.

---

