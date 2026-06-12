---
title: "Broken Dependencies"
date: 2012-06-06
forum: General Help
---

### Post by klokwyze on 2012-06-06
I'm trying to setup & configure my home Ubuntu box for SSH access. I honestly don't care if it's with OpenSSH-Server(is this the only option?). As you can see, I am getting the following dependency errors. What steps can I take in order to resolve this?

> root@LINUXBOX:~# apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openssh-server: Depends: openssh-client (= 1:5.3p1-3ubuntu3) but 1:5.3p1-3ubuntu7 is to be installed
E: Broken packages


> root@LINUXBOX:~# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"


---

### Post by raja.genupula on 2012-06-06
open  your terminal and type this

```
sudo apt-get install -f
```

---

### Post by klokwyze on 2012-06-06
> **raja.genupula said:**
> open  your terminal and type this

```
sudo apt-get install -f
```

Still getting the same error listed in my original post. Please advise.... should I just update to 12? :)

```
root@LINUXBOX:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by diesch on 2012-06-06
Run
```
apt-get update
``` and try again. If it still doesn't work please post the output of
```
apt-cache policy openssh-server openssh-client
```

---

### Post by klokwyze on 2012-07-08
```
root@LINUXBOX:~# apt-cache policy openssh-server openssh-client
openssh-server:
  Installed: (none)
  Candidate: 1:5.3p1-3ubuntu3
  Version table:
     1:5.3p1-3ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages
openssh-client:
  Installed: 1:5.3p1-3ubuntu7
  Candidate: 1:5.3p1-3ubuntu7
  Version table:
 *** 1:5.3p1-3ubuntu7 0
        100 /var/lib/dpkg/status
     1:5.3p1-3ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages

```

Here ya go.... any idea what the issue is?

---

### Post by diesch on 2012-07-08
Make sure you have enabled "Recommended updates" in the "Updates" tab of "Software sources" (or activated "lucid-updates" otherwise)

---

### Post by gyrolc on 2012-11-18
I had this same issue. The cause seems to be that openssh-client is too new of a version for openssh-server.

I did:
```

sudo apt-get remove openssh-client

```

followed by

```

sudo apt-get install openssh-server

```

to resolve the issue.

---

