---
title: "UFW script?"
date: 2009-07-16
forum: General Help
---

### Post by fantastic on 2009-07-16
I have a bunch of UFW settings that I've just dumped into a bash script so it keeps track of what rules I had and so I don't have to retype everything:

```
#!/bin/bash

# init the UFW
sudo ufw enable
sudo ufw logging on
sudo ufw default deny

# allow [user] access via SSH
sudo ufw allow from xxx.xxx.xxx.xxx to any port [port num]

# allow [user] access via remote desktop
sudo ufw allow from xxx.xxx.xxx.xxx to any port [port num]
sudo ufw allow from xxx.xxx.xxx.xxx to any port [port num]

[lots more rules ...]
```

Is this efficient of is there an easier way? :confused:

Am I missing something how UFW works?

The other reason why I do it this way is because all commands and settings have to be documented (for a non techie) to understand exactly what commands were used so they can "re-create" it should a techie not be here ](*,)

---

### Post by mcduck on 2009-07-16
You only need to run those commands once, not in every boot. That's the point of using UFW instead of writing your own iptables scripts. :)

If you need to check what rules you have then run "sudo ufw status", or if you want the output in iptables format "sudo ufw show".

---

