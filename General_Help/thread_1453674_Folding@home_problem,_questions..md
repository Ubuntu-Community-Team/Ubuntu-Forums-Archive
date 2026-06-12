---
title: "Folding@home problem, questions."
date: 2010-04-13
forum: General Help
---

### Post by undecim on 2010-04-13
I just set set up F@H follwing [https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu/HowTo](https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu/HowTo)

[s]I run it, and get a lot of this:
```
[19:23:20] + Attempting to get work packet
[19:23:20] - Connecting to assignment server
[19:23:23] + No appropriate work server was available; will try again in a bit.
[19:23:23] + Couldn't get work instructions.
[19:23:23] - Attempt #7  to get work failed, and no other work to do.

```

How do I get it to find a server?[/s]
nvm that part. It's working now.

Also, will it automatically use my ATI GPU if it can, or do I have to explicitly use the -gpu option? Will my ATI drivers get in the way?

Do onboard intel graphics do any good?

And finally, how intrusive will this be? I plan on running it on every computer in my house, including my siblings' and parent' (with their permission, of course), but how much RAM and CPU will it use? Can I assume it will it only use idle CPU cycles?

---

### Post by duanedesign on 2010-04-14
The Folding@Home client uses a very low priority to make sure all other programs, apps, etc. receive all the CPU power they need. The client will only use whatever processing power is left over to fold with. Because the client runs at low priority, the client should not cause the CPU governor to kick up the frequency. In other words, even though the client runs at 100% CPU usage, it should not cause the CPU frequency to go up, which keeps the fan slow and quiet. If this is not the case, then the frequency governor should be reconfigured. 

I dont see a gpu client for Linux on the [folding@home site]("http://www.stanford.edu/group/pandegroup/cgi-bin/edit/English/Main").

Might ask on the [folding@home forum]("http://foldingforum.org/") to see if anyone knows better.

Also there is a channel #ubuntu-folding on IRC freenode network. The team has a  [Launchpad group and mailing list]("http://www.launchpad.net/~folding-at-home") if the channel is quiet. 
-
-

---

### Post by undecim on 2010-04-14
Thanks. I'll definitely get on the folding forum IRC channel later.

---

