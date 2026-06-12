---
title: "Monitoring other users on the same machine"
date: 2009-07-20
forum: General Help
---

### Post by anlag on 2009-07-20
Yesterday, I needed to transfer some files from my local machine to a friend, so I made a guest account on my Ubuntu desktop and let him grab the stuff via scp. All good.

However, I was wondering if there's a convenient way to keep an eye on what he's doing, like what files he's downloading and how long they have left, etc. What I could think of so far:

* Using the System Monitor from the System->Administration menu, to see that data is still being sent.
* Using top or htop to see what processes the guest user is running.
* Running 'ps -u guest' for another way to see the processes.

I suppose these are okay, but with top/htop it takes looking the processes up by scrolling/sorting and that's a little inconvenient. Meanwhile, the ps command is quick, but doesn't give any detail. For instance, if the guest user is in the process of doing an scp transfer, ps will only tell me he's running scp and a process number, but no details. top/htop will tell me also what exact files are being transferred by listing the whole command.

I guess if I could get the same detail as top/htop gives, but with the convenience of ps, I would be happy. But I'm sure there are other nice ways of doing it too. As a test, I installed Wireshark but frankly that's a little overwhelming for a simple task as this.

Any input appreciated, cheers!

---

### Post by kidders on 2009-07-21
Hi there,

There are lots of ways of keeping tabs on what people are doing on your box. As you've noticed, none of them really offer a nicely joined-up solution though. :-( One pretty low-tech tweak you could make is to replace **scp** with a short shell script. For example ...```
mv /usr/bin/scp /usr/bin/scp.real
cat << EOF > /usr/bin/scp
#!/bin/bash
echo \$@ >> /tmp/scplog
/usr/bin/scp.real \$@
EOF
chmod 755 !$
```
Pasting that into a terminal (as root) would cause your system to start logging file transfers to /tmp/scplog. In practice, you'd probably want to do something more elaborate, I suppose, but you get the idea.

> **anlag said:**
> with top/htop it takes looking the processes up by scrolling/sorting and that's a little inconvenient.Have you tried **top -u username** to reduce the amount of garbage you have to scroll through?

> **anlag said:**
> the ps command is quick, but doesn't give any detail**ps** has lots of options for controlling process selection & output formatting. For example, **ps -u username -o "%c %a"** should give you the names of all processes (and all their arguments) running as a given user.

If you're interested in more than file transfers, you might like to try this ...[LIST]
[*]Run **mkfifo /tmp/foobar && script -f /tmp/foobar**. The terminal should just sit there & hang.
[*]Open another terminal window and run **cat /tmp/foobar**.
[*]Now you should be able to use the second terminal session to watch everything that happens in the first.
[/LIST]

The only use I've ever had for this sort of thing is remote assistance (so a computer's owner can see how I go about solving whatever problem they're having). To spy on someone, I suppose you could alter your guest user's .bashrc so every time he starts a session, everything he does gets logged automatically.

Anyhow, with any luck there's something here you didn't already know.

---

