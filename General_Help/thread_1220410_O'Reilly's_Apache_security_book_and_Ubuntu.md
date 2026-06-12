---
title: "O'Reilly's Apache security book and Ubuntu"
date: 2009-07-22
forum: General Help
---

### Post by tonyoz on 2009-07-22
In O'Reilly's 'Apache Security' book it states to set Apache binary file permissions and make sure only root has write access by doing:

# chown -R root:root /usr/local/apache
# find /usr/local/apache -type d | xargs chmod 755
# find /usr/local/apache -type f | xargs chmod 644
# chmod -R go-r /usr/local/apache/conf
# chmod -R go-r /usr/local/apache/logs

I have installed lamp-server on Ubuntu desktop, so the above doesn't seem to make much sense as it looks like, in Ubuntu, the above locations are not used by Apache2? Also, I presume that sudo$ is the equivalent of # in the above commands?

Could someone please advise how I can do the equivalent of the above in a terminal window in Ubuntu?

Also is there a reference someone knows of somewhere on how to configure and secure Apache which has a Ubuntu focus?

Regards

---

