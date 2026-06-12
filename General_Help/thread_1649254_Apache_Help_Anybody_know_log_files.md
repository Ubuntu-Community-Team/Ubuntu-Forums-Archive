---
title: "Apache Help: Anybody know log files?"
date: 2010-12-19
forum: General Help
---

### Post by 0949er on 2010-12-19
Just curious if anybody is familiar with Apache 2x and log files. I am trying to figure out if there is a way to ignore a specific IP address from the logs all together? All I can find is this line:

```

SetEnvIf Remote_Addr "127\.0\.0\.1" dontlog

```I do not know where to put that, and if I place it in my .conf file, it does not exclude 127.0.0.1 from logs. any ideas?

---

### Post by 0949er on 2010-12-20
actually to answer my own question I was forgetting the second part to that code, which is:

```

# Log what remains
        CustomLog logs/access_log common env=!dontlog       

```

oops, haha! works now :)

---

