---
title: "White Screen After Log In, (attempted to apply compiz)"
date: 2009-08-04
forum: General Help
---

### Post by madmixx928 on 2009-08-04
I am a very new user to the whole ubuntu/linux based os however i have been playing around with it for the past few days when i finally decided to try out compiz. However when i thought i had applied compiz and restarted ubuntu after i log in my desktop appears for a brief second than follows to a blank white screen with the cursor.

THe steps i took in order to set up compiz were the following (i feel like the porblem may have arose from my procedures)
---I went to Add/Remove applications, searched for compiz than selected the Compiz desktop effects and settings along with the COmpiz Fuson Icon. I than click apply changes. I than went to system-->preferences-->start up. In start up Name: Compiz Fusion
and entered fusion-icon for the command, than finally clicked ok. After doing all this i restarted Ubuntu enter my username&pass than it proceeds to the white screen and eventually crashes after a bit of duration

So far i have tried the system recovery when ubuntu boots but this still has not fixed the problem. If anyone could point me in the right direction or help I would greatly appreciate it

Thanks in advance!

---

### Post by dcstar on 2009-08-05
> **madmixx928 said:**
> I am a very new user to the whole ubuntu/linux based os however i have been playing around with it for the past few days when i finally decided to try out compiz. However when i thought i had applied compiz and restarted ubuntu after i log in my desktop appears for a brief second than follows to a blank white screen with the cursor.

THe steps i took in order to set up compiz were the following (i feel like the porblem may have arose from my procedures)
---I went to Add/Remove applications, searched for compiz than selected the Compiz desktop effects and settings along with the COmpiz Fuson Icon. I than click apply changes. I than went to system-->preferences-->start up. In start up Name: Compiz Fusion
and entered fusion-icon for the command, than finally clicked ok. After doing all this i restarted Ubuntu enter my username&pass than it proceeds to the white screen and eventually crashes after a bit of duration

So far i have tried the system recovery when ubuntu boots but this still has not fixed the problem. If anyone could point me in the right direction or help I would greatly appreciate it

Thanks in advance!

The problem is probably in your user profile and the program you are starting.

Boot up into text mode, log in and then edit the following file and remove the Compiz stuff you are autostarting:

```
nano .config/autostart
```

Then:

```
sudo init 6
```

---

