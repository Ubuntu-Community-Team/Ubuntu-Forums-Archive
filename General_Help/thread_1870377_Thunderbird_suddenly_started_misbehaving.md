---
title: "Thunderbird suddenly started misbehaving"
date: 2011-10-27
forum: General Help
---

### Post by dryder on 2011-10-27
Hi,
Ubuntu 10.04-1 AMD64
Thunderbird 3.1.15

Thunderbird has suddenly developed problems:
1. thunderbird-bin process does not close with thunderbird
2. the lock file remains until thunderbird-bin process is killed
3. under the type of file, lock is 'link (broken)'
4. there is a lot of network activity when thunderbird is closed but thunderbird-bin process is running.

I saved the profile and started a new one. On a brief trial the problem disappeared. (As the new profile didn't have all my mail, I deleted it and reverted to my original profile.)

Can anybody suggest any repairs I can try please? I've searched the net and can't find anything.

Help much appreciated as this is used for business mail.

David

---

### Post by mallansohn on 2012-04-08
I have exactly the same problem !

I noticed activity on my internet connection though there was no reason for it (no programs that should be connecting).

This 'residual' activity  is distributed like this : Download : +/- 45 Ko/sec;  Upload : +/- 6 Ko/sec

netstat -apt  gave me information that thunderbird-bin had a connection established on local port 35643 though the program was closed !

Killing the process stopped the download/upload flow; but this behavior happens any time i start/close thunderbird.

For information, i'm running thunderbird 3.1.20 on Ubuntu 10.04.

---

