---
title: "Error when installing freeradius-mysql (Jaunty)"
date: 2009-12-12
forum: General Help
---

### Post by fulat2k on 2009-12-12
Hi folks,

I'm getting the following error when installing freeradius-mysql and freeradius in Jaunty:

```
# apt-get install freeradius freeradius-mysql
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freeradius-mysql: Depends: freeradius (= 2.1.0+dfsg-0ubuntu4) but 2.1.0+dfsg-0ubuntu4.1 is to be installed
E: Broken packages
```

Any idea how I can fix the dependency/broken packages problem?  I can't upgrade to Karmic for the time being.


Thanks.

---

### Post by Vishnu V on 2009-12-13
try this
Go to synaptic package manager and click on Edit->Fix broken packages and apply the changes
Now install freeradius-mysql

---

