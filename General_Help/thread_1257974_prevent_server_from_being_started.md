---
title: "prevent server from being started"
date: 2009-09-04
forum: General Help
---

### Post by stephan0h on 2009-09-04
Hi,

I've installed PostgreSQL recently - I'm not needing it on a daily basis but I want to play with it. So i don't need the server running all the time. 

How can i configure ubuntu, so that i can start the server manually  - and it's not started at bootup time?

thanks,
stephan

---

### Post by geirha on 2009-09-04
Disable it under System -> Administration -> Services. That should make it not automatically start during boot. Start it manually with ```
sudo /etc/init.d/postgresql start   #And stop to stop it again
```

---

### Post by shylent on 2009-09-04
It should show up in System->Administration->Services. You can untick it there. To start it manually you can, for example, run it using the init script like this - /etc/init.d/postgresql-8.3 start (probably want to do it with elevated privileges - use sudo).

---

### Post by stephan0h on 2009-09-04
i found this: [http://www.cyberciti.biz/faq/howto-runlevel-configuration-tool-to-start-service/](http://www.cyberciti.biz/faq/howto-runlevel-configuration-tool-to-start-service/)

it nicely describes update-rc.d and rcconf. 

thanks,
stephan

---

