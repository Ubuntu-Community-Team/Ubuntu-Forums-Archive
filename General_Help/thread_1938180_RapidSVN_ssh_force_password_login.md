---
title: "RapidSVN ssh force password login"
date: 2012-03-09
forum: General Help
---

### Post by Frozen Forest on 2012-03-09
I'm unable to login on a ssh+svn server with rapidsvn (Subclipse work fine), each time I try to connect to I get this message
```
Error: Error while updating filelist (To better debug SSH connection problems, remove the -q option from 'ssh' in the [tunnels] section of your Subversion configuration file.)
```I'm guessing the problem is related to that the server uses both key and password authentication, something I noticed when login into the server by ssh alone. To be able to get it working is the following command required.
```
ssh -o PubkeyAuthentication=no user@...
```How do you force svn to use this command or is there an other workaround? Where is the -q option looked in ~/.subversion but haven't found anything.

---

