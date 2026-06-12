---
title: "No ircd connections under Ubuntu"
date: 2012-06-06
forum: General Help
---

### Post by Brimwylf on 2012-06-06
Hello everyone.
I have a problem with using Unreal ircd 3.2 on Ubuntu.
I programmed a bot a few years back for my firm (nothing harmful or anything of the sorts, just a bot with a huge database of terms that gets updated daily by each employee). What initially started as fun and games for me eventually turned into a habit for most of the employees at  my firm. We now have about 50 bots running all day long (one per employee, more or less). We even use IRC to communicate internally because of this, who needs all that hocus-pocus skype anyway? :)

Now, the problem is this: I moved my computer(s) to Ubuntu and the bots are not connecting to the server anymore (I use my own server for this). This is definitely something related to Ubuntu, because it worked without a problem before my switch. Like, 2 hours before my switch.

My server is behind a DMZ-ed router, the irc port is open (and visible from the outside), I use the same (exact same) config that I used on the previous distribution, and even the same sources, I just recompiled the ircd on Ubuntu. Basically, what I did was erase my old distribution, install Ubuntu, recompiled Unreal, ran it, and got nothing from the bots. I can connect to my server just fine with a normal irc client (locally or from outside the DMZ). The bots have been restared daily (just a simple irc bot really, the "power" comes from the actual databases), but still nothing.
I'm not 100% sure this is just Ubuntu's fault, or a whole mass of stuff happening in addition to moving over to Ubuntu, but I'm going nuts here. Tried different config options, reset my router. I tried whatever I could think of, including another ircd (hybrid), and that didn't receive connections either.

Is there something I'm missing? Does Ubuntu have some sort of firewall layer, anything? Is there something I could and should check? I'm talking a basic (K)ubuntu install here. I didn't set any iptables, the router was (initially) in the same state as it was with the other distribution. The bots just don't connect (even checked Unreal's ircd.log and all I have in there are my own connections and the connections from the other employees, but no bots). So, what is it? What does Ubuntu do that the other distro does not?

So, please, if anyone has any suggestions, I'd love to hear them. It's not such a huge deal, but I honestly don't want to rewrite the bot because of this.

P.S. The sources are long lost, so making any modifications to it (or checking snippets of code) is out of the question.

---

