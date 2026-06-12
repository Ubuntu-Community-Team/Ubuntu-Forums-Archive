---
title: "Installation of CURL failed"
date: 2010-03-17
forum: General Help
---

### Post by uShafee on 2010-03-17
The following:
```

sudo apt-get install php5-curl

```

gives this error
```

user@domain:~$ sudo apt-get install php5-curl
[sudo] password for shafee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-curl: Depends: php5-common (= 5.2.10.dfsg.1-2ubuntu6) but 5.2.10.dfsg.1-2ubuntu6.4 is to be installed
E: Broken packages
user@domain:~$ 

```

what is going on?

---

