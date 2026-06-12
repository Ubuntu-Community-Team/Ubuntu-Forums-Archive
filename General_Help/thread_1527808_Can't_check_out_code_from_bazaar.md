---
title: "Can't check out code from bazaar"
date: 2010-07-09
forum: General Help
---

### Post by afrodeity on 2010-07-09
```

bzr branch lp:~duanedesign/+junk/clicompanion
Proxy could not open connnection to bazaar.launchpad.net:  Unauthorized
ssh_exchange_identification: Connection closed by remote host
bzr: ERROR: Connection closed: Unexpected end of message. Please check connectivity and permissions, and report a bug if problems persist. 

```

My proxy is turned off. There is no local proxy as far as I can see. Anyone see this before? Is it my ISP?

UPDATE: I was wrong, forgot about an old proxychains setting which redirected ssh traffic via a proxy on port 22.

---

### Post by duanedesign on 2010-09-11
Their is a new version of CLI Compainon. If you would like to check it out you can [get the .deb here]("https://launchpad.net/clicompanion").

You can also add the PPA to receive updates when they get uploaded. The commands for that are:

```
sudo add-apt-repository ppa:clicompanion-devs/clicompanion-nightlies
```

```
sudo apt-get update; sudo apt-get install clcompanion
```

---

