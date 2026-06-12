---
title: "unable to SSH in using keys on Ubuntu 9.04"
date: 2009-10-06
forum: General Help
---

### Post by CharlesA on 2009-10-06
Hiya,

I ran into this yesterday when I moved the server to a different room. I was able to get in with ssh only if I used my acct password. I disabled that since I wanted to just use a private key to login instead of the password for security reasons.

First time it happened I was able to recreate the key with ssh-keygen and import/convert it using puttygen.

Second time, I recreated the keys many times with no dice.

I ended up doing a reinstall of the OS, but I was wondering if there was anything else I could have done.

The error I was getting was: "Server refused our key." :confused:

Thanks for any help.

---

### Post by KeyserSoze93 on 2009-10-06
Have you made sure that both versions of SSH are the same (or atleast that they are both post-2008 ssh security fix)?

I dig ssh keybased authentication, but it's sometimes a hassle to set up.

Make sure both machines have the packages upgraded etc.

Are the keys rsa or dsa? Because on some machines, I ended up simply using DSA till I could make it work (ssh-keygen -t dsa; scp ~/.ssh/id_dsa.pub etc...)

---

### Post by CharlesA on 2009-10-06
Hrm. Maybe that's what I was doing wrong. I was only running: 

```
ssh-keygen
cat id_rsa.pub >> authorized_keys2
```

I'd copy the id_rsa file to a samba share to get it over to my Windows machine and import it into PuTTY with puttygen.

I set the server up to use SSH2 (I think anyway.)

The annoying part was that it worked fine before I installed DenyHosts, so I'm guessing that probably had something to do with it.

---

### Post by Giblet5 on 2009-10-06
Try turning on debugging mode.

Example: ```
ssh -vvvvv loungelizard@pron.quantico.fbi.gov
```

This will dump HUGE quantities of information about the session and will likely help you or your IT guys figure out what's missing.

If you're doing this over a DSL/Cable connection, find out what your MTU is on your router. An MTU of less than 1500 *may* cause enough fragmentation of packets that the handshake might not complete.

---

### Post by CharlesA on 2009-10-06
Heh, I'm the IT guy. I was connecting locally over my home network. That's what was so odd about it.

I am also connecting with PuTTY from a Windows box.

---

### Post by Giblet5 on 2009-10-06
> **CharlesA said:**
> Heh, I'm the IT guy. I was connecting locally over my home network. That's what was so odd about it.

I am also connecting with PuTTY from a Windows box.


The -vvvvv thing is the key to figuring it out.

I had a similar problem going from Dapper to Jaunty. There's still an open Launchpad bug report on it.

I wonder how many klaxons are sounding over that command example. Those guys have a crummy sense of humor. :P

---

### Post by CharlesA on 2009-10-06
Thanks for the advice. I ended up wiping the drive and reinstalling since I was just playing around with it for a while on the live machine (instead of using my copy in my VB like a smart person).

I'll give it a shot if it happens again. 

I didn't notice the URL that you were SSHing to. Lol.

---

