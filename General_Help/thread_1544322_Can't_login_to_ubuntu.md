---
title: "Can't login to ubuntu"
date: 2010-08-02
forum: General Help
---

### Post by Metalclay on 2010-08-02
When I turn on the pc, it displays a sorts of odd code, which it has done since I installed Lucid. Now however, for whatever reason, it wants me to login from one of those black screens with code.

It displays the ubuntu version at the top and under that my computer's name and it asks for user and at the side of that it says ttyl.

So, I type in the user, then the password, and it displays: Welcome to Ubuntu!

Which would be great if I knew how to navigate from that terminal-like screen. However, I don't and I don't want to. I just want to get to my regular desktop with the tool bar, and all those user friendly visuals.

Any ideas on how to fix this? It was doing this yesterday, but I just restarted and it took me to my desktop like it usually always did. But today, it just doesn't want me to get there and instead takes me to this terminal-like environment.

Thanks.

---

### Post by WorMzy on 2010-08-02
Try running
```
startx
```

Does that get you to your desktop environment? If not, what errors does it produce.

If it gets you to your desktop environment, then copy and paste the last ~20 lines from the .xsession-errors here.

---

### Post by Metalclay on 2010-08-02
Yes! worked.

I had read to try that somewhere else, but I wanted to make sure. Since I installed this for my mom who doesn't know a lick about computers, and she's getting used to ubuntu, so I didn't want to run the risk of completely messing up the installation.

Thanks again.

---

