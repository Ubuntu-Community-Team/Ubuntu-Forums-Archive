---
title: "Script to replace the ip address in a config file with the current ip address"
date: 2009-07-22
forum: General Help
---

### Post by jaders on 2009-07-22
I need an example of a script that would find the current ip address of a machine and then import it into a config file to replace a different ip address.

What I have so far is just pulling the current IP. 

```
ifconfig | perl -lne'/dr:(\S+)/&&print$1'
```

This is the line in the config file that I would need to change.

$config['root_url'] = 'http://10.11.102.120';

Any help would be appreciated.

---

