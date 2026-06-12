---
title: "download repository indexes get: &quot;Bizarre Error&quot;"
date: 2010-09-03
forum: General Help
---

### Post by Ronok on 2010-09-03
Hi, 
Got a **"Bizarre Error"**

went to **SYSTEM > administration > Update Manager**...

saw something about security update for "Wget"
after getting that downloaded 
hit the refresh button to see if there were any outstanding updates...

got this ERROR:

"
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
 - - - 
Bizarre Error - File size is not what the server reported 0 298862Failed to fetch [http://ubuntu.cn99.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2](http://ubuntu.cn99.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.
"

Recently I have Been getting a lot of some variations of this ERROR:
"**Failed to Fetch** http something UBUNTU something Hash Sum Mismatch"

My strategy for now is to go to:
**SYSTEM > administration > Update Manager > Settings > Ubuntu Software > Download from > ** (then) (change to another server)

Just Worry that this machine is not getting its updates properly
thanks for any input or advice
Ronok

uname -a = 
(Pure Ubuntu 9.10 Linux)
2.6.31-22-generic #63-Ubuntu SMP Wed Aug 18 22:54:26 UTC 2010 i686 GNU/Linux



[[SIZE="1"]http://www.gongkuo.com/index.htm[/SIZE]]("http://www.gongkuo.com/index.htm")

---

### Post by Ronok on 2010-09-23
I am going to Mark as "SOLVED" [SIZE="1"](but...[/SIZE]*[SIZE="1"])[/SIZE]

Solved Because in general when running:
SYSTEM > administration > **Update Manager**...
and receiving Errors something like:
"Failed to Fetch... something or Could not download all repository indexes"

it Simply can be Solved by going to:
**SYSTEM > administration > Update Manager > Settings > Ubuntu Software > Download from >** (then) (change to _another / different server_)

ok I am all :) Updated  
But *
Just Thought I would share this Error

[Thanks Ronok]("http://www.gongkuo.com/")

---

