---
title: "set datasource when configuring tungsten fan in replication in ubuntu for a mysql dat"
date: 2012-01-11
forum: General Help
---

### Post by Rumbi on 2012-01-11
What steps will reproduce the problem?

I am following this tutorial on seting up fan-in or multi-source replication:
[http://datacharmer.blogspot.com/2011/08/usability-improvements-in-tungsten-204.html](http://datacharmer.blogspot.com/2011/08/usability-improvements-in-tungsten-204.html) The main problem is in setting the datasource in this step --datasource=qa_r4_continuent_com

I know that the datasource is different from the database name, but how do I view it for the mysql database I am using. Was it automatically created, since research tells me that it is used when executing queries on a database. If so, how do I view the datasource in ubuntu?

If it is not automatically created, how do I set it or how do I create it? Could you please post a step by step tutorial or provide a reliable link to
 a tutorial that shows me how to resolve this problem.

Rumbi


What do you see instead?
ERROR >> localhost >> You must specify a datasource alias or datasource confi
ERROR >> localhost >> There was a problem parsing the arguments
ERROR >> localhost >> You must specify a datasource alias or datasource confi
ERROR >> localhost >> There was a problem parsing the arguments

tungsten-replicator/bin# $TUNGSTEN_BASE/tungsten/tungsten-replicator/bin/trepctl status
pendingExceptionMessage: Client handshake failure: Client response validation failed: Client requested non-existent transaction: client source ID=localhost seqno=86 client epoch number=65


...

What version of the product are you using...
tungsten-replicator-2.0.4 Binary Build

On what operating system?
turnkey
 32-bit ubuntu virtual machine 
...

---

### Post by airplanesimen on 2012-01-11
> **Rumbi said:**
> What steps will reproduce the problem?

I am following this tutorial on seting up fan-in or multi-source replication:
[http://datacharmer.blogspot.com/2011/08/usability-improvements-in-tungsten-204.html](http://datacharmer.blogspot.com/2011/08/usability-improvements-in-tungsten-204.html) The main problem is in setting the datasource in this step --datasource=qa_r4_continuent_com

I know that the datasource is different from the database name, but how do I view it for the mysql database I am using. Was it automatically created, since research tells me that it is used when executing queries on a database. If so, how do I view the datasource in ubuntu?

If it is not automatically created, how do I set it or how do I create it? Could you please post a step by step tutorial or provide a reliable link to
 a tutorial that shows me how to resolve this problem.

Rumbi


What do you see instead?
ERROR >> localhost >> You must specify a datasource alias or datasource confi
ERROR >> localhost >> There was a problem parsing the arguments
ERROR >> localhost >> You must specify a datasource alias or datasource confi
ERROR >> localhost >> There was a problem parsing the arguments

tungsten-replicator/bin# $TUNGSTEN_BASE/tungsten/tungsten-replicator/bin/trepctl status
pendingExceptionMessage: Client handshake failure: Client response validation failed: Client requested non-existent transaction: client source ID=localhost seqno=86 client epoch number=65


...

What version of the product are you using...
tungsten-replicator-2.0.4 Binary Build

On what operating system?
turnkey
 32-bit ubuntu virtual machine 
...

Ehm, sorry, u posted this in "absolute beginner talk". try to move it to the main category :? I didnt understand a beep of what you tried to say, sorry :(

---

### Post by oldos2er on 2012-01-11
Moved to General Help.

---

