---
title: "firewall"
date: 2012-02-01
forum: General Help
---

### Post by johntd on 2012-02-01
I run Ubuntu 11.10 with with UFW as a firewall, at the moment I just let it run as is, I have read about ssh and was wondering if I should activate this or just leave things as they are, as you may have guessed I am a recent convert from Win 7 so most of this is new to me. Many thanks for your time John

---

### Post by Paqman on 2012-02-01
Ssh is a protocol for connecting to a remote machine, it's not a firewall. If you've set up a really restrictive firewall and want to use ssh to talk to the machine (which is a good idea) then you'll need to enable it in your firewall. Using a non-default port for ssh isn't a bad idea either. The default is 22.

---

### Post by johntd on 2012-02-01
Many thanks for that info I will forget about it

---

### Post by seawolf167 on 2012-02-01
Just to add since you mentioned you are new, you can use the graphical version of UFW to make it a little easier in the future.

```
sudo apt-get install gufw
```

then [ALT][F2] and type in gufw

---

