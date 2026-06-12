---
title: "I globered my WINS samba server, help"
date: 2010-08-18
forum: General Help
---

### Post by ulao on 2010-08-18
So I have been using samba with WINS enabled for a few years now. I know all setting in my smb,conf were and still are fine. For some unknown reason my samba shares got wacked. I have no idea what cause it but I could not fix it.  So I decided to take the plunge and install a smb client. I remember thinking, I'm going to regret this... After the install of system-config-samba It would not run, I saw a few forums talking about missing dependencies  and they didnt help. Then I came across this suggestion.

```

 sudo aptitude install samba samba-common-bin system-config-samba smbfs smbclient
```


After words my permissions got fixed. So I was quite happy. and Wins was working great with all shares set up correctly. Than after a reboot WINS was not working. So I tried to clear out the WINS data files and restart smbd, but now it wont create my WINS.dat file. I dont see anything in the logs that helps me here, any ideas?

Currently my shares are good, samba is working fine, but WINS will not works.  From a windows box I get "There are no entries in the list." from a net view.

---

### Post by ulao on 2010-08-18
I guess I just learned something. smbd does not control WINS nmbd does... So I restarted nmbd and the wins files are back but my shares are down again. 

why must I start nmbd after boot up, and then restart smbd, is this a 10.04 bug?

---

