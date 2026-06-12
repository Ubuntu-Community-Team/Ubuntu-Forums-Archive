---
title: "tree putting out garbage"
date: 2010-09-15
forum: General Help
---

### Post by josephmc on 2010-09-15
I was getting nasty output with tree and didn't see anything in the forum so I thought I would post my solution. It was using the wrong charset. 

Run the following command as your normal user
```
echo "alias tree='tree  --charset ISO-8859'" >> ~/.bashrc

```
log out then log back in so it loads the changes

this is only for that user so if you want to do it system wide put it at the end of /etc/bash.bashrc

---

