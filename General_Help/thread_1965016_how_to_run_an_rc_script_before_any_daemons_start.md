---
title: "how to run an rc script before any daemons start?"
date: 2012-04-24
forum: General Help
---

### Post by Skaperen on 2012-04-24
What is the appropriate way, with the upstart system, to run a script I will write, before ANY of the daemons start up, but after the network is configured?

---

### Post by JKyleOKC on 2012-04-24
To the best of my knowledge, what you ask for is simply not possible. Upstart attempts to run all of the startup scripts at the same time, with safeguards built in to assure that required items have started before things that require them are launched. These safeguards assure that the network doesn't get brought up before all of its requirements are in place, and some of those requirements may be scheduling daemons.

If your script requires that the network be up, then it cannot run any earlier -- and if the network requires one or more daemons to be running, they will be before your script begins.

If the script doesn't require the network, then you could set up its Upstart triggers and requirements to run at most any stage you want. However you have to remember that the filesystem that contains it must be mounted before the script can run. For the newcomer to parallel processing, Upstart can be a true can of worms -- very active wrigglers! It can be a veritable minefield of unexpected consequences.

---

### Post by Skaperen on 2012-04-25
The script augments the network configuration by adding additional IP addresses.  Daemons that listen on the network will need to be started after this is done.

Daemons that are not network daemons, perhaps needed to actually run the network, can start before this.

---

### Post by kevdog on 2012-04-25
Couldn't you modify specific daemons' start up scripts that would depend on your particular service being run first?  This could be done with a preup or depends statement (possibly). A little trial an error would go a long way here.

---

### Post by Skaperen on 2012-04-25
> **kevdog said:**
> Couldn't you modify specific daemons' start up scripts that would depend on your particular service being run first?  This could be done with a preup or depends statement (possibly). A little trial an error would go a long way here.
I guess that makes sense.  At least I can do this for the critical ones that need all the IPs.  Then anything the network depends on would not depend on the network or my scripts.

---

### Post by kjohri on 2012-04-25
You can start the relevant daemon after a network interface is configured. The following link gives more information.

[Starting a network server after communication interface is up]("http://www.softprayog.in/troubleshooting/starting-a-network-server-after-communication-interface-is-up")

---

