---
title: "cannot mount ipod touch: does not respond to ping"
date: 2009-08-10
forum: General Help
---

### Post by pvatterott on 2009-08-10
Hey everyone,

I am trying to sync my music on my ipod touch with Rhythmbox (or Amarok if this proves difficult); however, I am having issues mounting my jailbroken 2G ipod touch on ubuntu 8.10. After installing the ipod-convenience package, I enter the command:
```

ipod-touch-mount
```and receive the output:
```

iPod is not responding to pings at 192.168.1.107.
Please set the environment variable IGNOREPING if you want to ignore this.
```The ip address is set to static and I can manually ssh into the ipod but it does not respond to ping from the terminal.

In response to the message about IGNOREPING I attempted setting the environment variable using:

```
export IGNOREPING=1
```which set the variable as confirmed by running env, but failed in solving my problem; however, I am not sure if this was the correct method.

Google did not help me, nor did the man page, or ipod-conveniences launchpad site.

Does anyone have any insights as to what my problem could be, or a different method for solving it?

Thanks for your time

---

