---
title: "Upstart: sequential hook before entering runlevel?"
date: 2011-09-16
forum: General Help
---

### Post by radu.c on 2011-09-16
Hi,

I have a very specific problem and I've been fighting Upstart all night with no success.

I my particular case, I have a server with a bunch of PXE booted clients. The data for the clients is stored in MySQL. When I shut down the server, before anything happens, I need all the PXE clients to be turned off as well. In the old, sequential world of sysvinit this was a piece of cake: just put the remote shutdown script early in the sequence, before networking, portmap, nfs, mysql go down. This was ok even if it took 10 minutes for all the clients to go off (but usually 30 seconds would be enough).

With upstart I can't for the life of me get the clients to shutdown before the server. I managed to get the script executed before mysql went down, but that isn't enough, as it seems that the network and/or other support stuff that the PXE clients REALLY NEED goes down, so they NFS mounts go up in smoke and they never power off. They will power off as soon as the server is back up though.

The closest I got to getting what I want is this:

```

kill timeout 70

start on runlevel [016] and (stopping mysql or stopping portmap or stopping idmapd or stopping statd)

task

exec the-script-that-shuts-clients-down.sh

```

The script tells all the machines to shut down then keeps an eye on them (sending pings once a second), and only when either they're all down, or the script gets bored and gives up, should the server continue the shut down sequence.

Now, with Upstart, my script gets killed after about 7 seconds. Even with the 70 second timeout as above.

Ideally, I'd like to execute that script _before_ anything else is triggered by the runlevel switch, but Google says I'm out of luck on this one. There's NO SEQUENTIAL mechanism in Upstart - even "backwards compatibility" rc is executed in parallel with the rest of the upstart services.

Any ideas on this one? I'm running Ubuntu 10.10.

Thanks.

---

### Post by radu.c on 2011-09-19
Answering to myself:

(Also on Ask Ubuntu: [http://askubuntu.com/questions/61643/sequential-hook-before-entering-runlevel/62192#62192](http://askubuntu.com/questions/61643/sequential-hook-before-entering-runlevel/62192#62192))

I managed to solve my problem with this:

```

kill timeout 70

start on runlevel RUNLEVEL=[016] PREVLEVEL=[2345] and (starting rc RUNLEVEL=[016] or stopping mysql or stopping portmap or stopping idmapd or stopping statd)

task

exec the-script-that-shuts-clients-down.sh

```

Well, almost, because it looks like Upstart has a little bug that is specific to hooking on rc. At least in Ubuntu 10.10 it does. I don't have an 11.04 at hand to confirm it.

The work around right now looks like this:

In *the-script-that-shuts-clients-down.sh*, before exiting I do

```

touch /etc/init/my-job.conf

```

where my-job.conf contains the stuff above. So far it unstuck rc from start/starting everytime.

Another catch is that if I write **starting rc** rather than **starting rc RUNLEVEL=[016]** then upstart gets stuck on rc at boot too (and the same touch command unsticks it).

:popcorn:

---

### Post by dcstar on 2011-09-20
Good work on this, I have been trying to figure out how to cleanly shut down my running VMware Player VMs before Ubuntu cuts off VMWare Player at the knees with its fast shutdown. 

I may have to find the time to try out this method!

---

