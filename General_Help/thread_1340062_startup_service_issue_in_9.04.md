---
title: "startup service issue in 9.04"
date: 2009-11-28
forum: General Help
---

### Post by Anoop.kulkarni on 2009-11-28
Hi,

I have to intall Jaxer service (an AJAX serer) as startup on my Ubuntu 9.04. I have asked this question to Jaxer community, did not get a satisfactory reply so am posing this to the Ubuntu Forum.

Here is my description of the problem.

1. The jaxer service can be enabled and disabled through the scripts start.sh and stop.sh
2. start.sh works when invoked from a terminal either as root or normal user
3. have created a Jaxer service called 'jaxer' under /etc/init.d and added with update-rc.d
4. "/etc/init.d/jaxer start" works just fine from a terminal
5. Now the problem. When I restart the machine, the service attempts to start and then fails (exits).
6. Again, if I open a terminal and run /etc/init.d/jaxer start, it runs just fine.
7. I have ensured that the update-rc.d registers the service for run levels 2,3,4,5 at 90 (when most other services already start up)

My question:

Is there anything specific I need to do to ensure that this works? Also, what is technically the difference between the script running at startup time versus running from an interactive shell? btw, start.sh file starts with "#!/bin/bash" !

Is this Ubuntu specific for which someone is aware of a work around?

Many thanks
~anoop
--
Anoop Kulkarni, PhD

---

### Post by xbaez on 2010-02-01
> **Anoop.kulkarni said:**
> Hi,

I have to intall Jaxer service (an AJAX serer) as startup on my Ubuntu 9.04. I have asked this question to Jaxer community, did not get a satisfactory reply so am posing this to the Ubuntu Forum.

Here is my description of the problem.

1. The jaxer service can be enabled and disabled through the scripts start.sh and stop.sh
2. start.sh works when invoked from a terminal either as root or normal user
3. have created a Jaxer service called 'jaxer' under /etc/init.d and added with update-rc.d
4. "/etc/init.d/jaxer start" works just fine from a terminal
5. Now the problem. When I restart the machine, the service attempts to start and then fails (exits).
6. Again, if I open a terminal and run /etc/init.d/jaxer start, it runs just fine.
7. I have ensured that the update-rc.d registers the service for run levels 2,3,4,5 at 90 (when most other services already start up)

My question:

Is there anything specific I need to do to ensure that this works? Also, what is technically the difference between the script running at startup time versus running from an interactive shell? btw, start.sh file starts with "#!/bin/bash" !

Is this Ubuntu specific for which someone is aware of a work around?

Many thanks
~anoop
--
Anoop Kulkarni, PhD


Were you able to run Apache with the mod_jaxer?

did you compiled it?

---

### Post by Anoop.kulkarni on 2010-02-09
I can run it from the prompt - but not at boot time

---

### Post by warfacegod on 2010-02-09
I don't suppose there's an entry in Startup Applications for it?

Shot in the dark here but try setting a slight delay on the startup for it. Perhaps a dependency isn't starting fast enough during boot for it to start properly.

---

