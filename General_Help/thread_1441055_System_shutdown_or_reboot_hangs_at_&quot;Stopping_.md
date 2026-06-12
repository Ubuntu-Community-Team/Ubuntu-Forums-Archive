---
title: "System shutdown or reboot hangs at &quot;Stopping VPN Daemons&quot;"
date: 2010-03-28
forum: General Help
---

### Post by auh2o on 2010-03-28
An error has occured seemingly out of the blue that makes me unable to reboot or shutdown my computer with less than pushing the reset button or pulling the cord. I only get as far in the shutdown process as

```
* Shutting down ALSA...
* Stopping virtual private network daemon(s)...
```And there it freezes. If I wait long enough I will also get

```
[ 6480.512031] INFO: task sync:4672 blocked for more than 120 seconds.
[ 6480.512740] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
```But nothing more happens after that

I do have an OpenVPN connection set up, but I did that long ago, haven't used it recently, and haven't made any changes to it or other network settings for a long while.

What exactly is the name of the VPN daemon process? Why won't it shut down? I would sure appreciate any help, since as you can understand this is quite a nuisance.

---

