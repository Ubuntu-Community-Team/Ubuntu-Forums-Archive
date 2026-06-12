---
title: "ddclient resident in memory"
date: 2011-01-17
forum: General Help
---

### Post by Wtower on 2011-01-17
I can't understand the logic of ddclient. I got a server with dynamic ip that keeps disconnecting and renewing the ip regularly.

I tried ddclient as a daemon, having setup the conf and init.d files apparently properly. Fore some reason for which I cannot find anything in the logs, it seems that it frequently fails to update the ip on dyndns. If I execute it from the command line, it updates it ok. 

I got irritated with this behaviour and I decided to completely purge everything and start anew with the default configuration not as a daemon. I then made a cron entry (which btw for me seems a better way to do this anyway) in order to check and update. All fine, but what I really do not understand is, since it is not a daemon, what on earth is this process 'ddclient' running behind. It doen't hold too much mem, but why to have one more process up. I have double checked /etc/init.d, it is correct. It seems to remain resident when I execute it.

Does anyone have a clue why this happens?

Thanks

---

