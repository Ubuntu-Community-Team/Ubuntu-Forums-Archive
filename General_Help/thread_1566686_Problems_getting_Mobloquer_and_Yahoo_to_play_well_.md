---
title: "Problems getting Mobloquer and Yahoo to play well together"
date: 2010-09-02
forum: General Help
---

### Post by whitemagicwoman on 2010-09-02
So, I am relatively new to Ubuntu (a few weeks in).  I am running Lucid dual booted with Windows Vista at this point.  

I have installed the Mobloquer GUI for better privacy.  That seems to be  going pretty well, except that it is making it difficult for me to  connect to the yahoo chat server.  I am running Pidgin.  The other  servers I use (AIM, Google) use one IP address each for their chat  connections and I have whitelisted those addresses.  However, it seems  that Yahoo uses a different IP address every time.  Whitelisting  whatever IP it tried last doesn't work.  I tried to put in a range -  with that, Mobloquer would not start up at all - something about an  invalid IP mask.

I realize that this is the Ubuntu forum, not specific to Moblock (or  Mobloquer) but when I google problems with Mobloquer the results are  almost all here.  So, I hope that those with knowledge will chime in  anyhow.

Many thanks.

---

### Post by jre on 2010-09-05
The format for whitelisting ranges in /etc/blockcontrol/allow.p2p is
```
123.123.123.123-123.123.123.123
```

Alternatively you can whitelist the whole port, see the wiki, especially [https://help.ubuntu.com/community/MoBlock#How%20can%20I%20allow%20%28whitelist%29%20traffic%20on%20certain%20ports?](https://help.ubuntu.com/community/MoBlock#How%20can%20I%20allow%20%28whitelist%29%20traffic%20on%20certain%20ports?)

---

### Post by whitemagicwoman on 2010-09-23
Thanks, jre.  I gave this a try and will post back with the result.

---

### Post by whitemagicwoman on 2010-09-27
Okay.  So, I edited  /etc/blockcontrol/allow.p2p  to say:

```
67.195.160.0-67.195.160.255

# allow.p2p - allow list for blockcontrol
#
# This file contains IP ranges that shall not be checked.
# They must be in the PeerGuardian .p2p text format like this:
#   Some organization:1.0.0.0-1.255.255.255
# This is also true if your blocklists are in another format.
# Lines beginning with a hash (#) are comments and will be ignored.
#
# Do a "blockcontrol restart" when you have edited this file.
```And saved.  Then I typed 

```
sudo blockcontrol restart
```in the terminal.  It seems to be running fine now.  I will keep an eye on it for a few more hours (since this was always an intermittent problem, popping up when Yahoo would use a new IP address I hadn't whitelisted) and then mark it solved.

Thanks again jre!

---

