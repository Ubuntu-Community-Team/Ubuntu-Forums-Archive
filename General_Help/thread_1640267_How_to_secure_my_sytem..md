---
title: "How to secure my sytem."
date: 2010-12-07
forum: General Help
---

### Post by john-do on 2010-12-07
Hello all fellow Linux users,
I just installed Ubuntu about 3 days ago and all has been working well and I'm learning to use it more effectively every day.
The reason i installed Ubuntu was because I discovered that people i thought were close to me were remotely SPYING ON ME through my computer.Apparently they had access to all my documents And could even hear and see me through my Mic And Web cam.I was using windows 7 with avg anti virus and windows firewall.
I would like to be able to use my computer(with they Internet) without having to worry about people stalking me.I would like for it to be practically impossible for these scumbags to get anywhere close to my privacy.
Please help me do so...
I have a router which i connect to with wifi and I'm  running the latest version of ubuntu.

Bows of graciousness to any help I may come across.

---

### Post by Verbeck on 2010-12-07
ubuntu is pretty secure out of the box and if you haven't installed anything outside the repos (anything other than the software-center) then you're quite safe.

also, read the stickies in [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by pricetech on 2010-12-07
You need to be sure your router is secure also.  I suspect that my be where your "friends" got in.

Can you switch to wired ??

---

### Post by uRock on 2010-12-07
Hello and Welcome to the forums.

Turn on the built in firewall with this command in a terminal* **sudo ufw enable** 

This will block all incoming connections without hindering your ability to utilize the internet.

**[SIZE=1] To open a terminal, go in your menus to Applications> Accessories> Terminal.[/SIZE]*

---

### Post by 3rdalbum on 2010-12-07
> **uRock said:**
> Hello and Welcome to the forums.

Turn on the built in firewall with this command in a terminal* **sudo ufw enable** 

This will block all incoming connections without hindering your ability to utilize the internet.

What good will this do? Ubuntu doesn't listen for incoming connections by default anyway.

---

### Post by uRock on 2010-12-07
> **3rdalbum said:**
> What good will this do? Ubuntu doesn't listen for incoming connections by default anyway.
Then why does a port scan show open ports on a default install?

---

### Post by bodhi.zazen on 2010-12-07
There are no "significant" open ports. There  are open ports which listen only on localhost (X and CUPS come to mind) and there is also zeroconf

See:

[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)

[https://wiki.ubuntu.com/ZeroConfPolicySpec](https://wiki.ubuntu.com/ZeroConfPolicySpec)

With that said, the vast majority of Desktop users do not need to enable their firewall.

---

