---
title: "&quot;Child returned status 2&quot;, what is this?"
date: 2011-02-21
forum: General Help
---

### Post by dderolph on 2011-02-21
I'm running Ubuntu 10.04LTS as a virtual machine using VMware Player. I want to use Terminal to use tar to install VMware Tools for VMware Player per instructions at [http://www.vmware.com/support/ws55/d...html#wp1127214](http://www.vmware.com/support/ws55/d...html#wp1127214).  I'm getting the following error message. Can someone shed some light on this?


[COLOR="DarkOrchid"]david@ubuntu:~$ sudo tar zxpf /mnt/cdrom/VMwareTools-8.4.5-324285.tar.gz
[sudo] password for david: 
tar: /mnt/cdrom/VMwareTools-8.4.5-324285.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
david@ubuntu:~$[/COLOR]

---

### Post by coolbeans777 on 2011-02-21
You are in your home directory, try using cd to go to the directory where the tar.gz file is downloaded.  If you dont understand how to use cd google it.

---

### Post by Habeouscorpus on 2011-02-21
That usually means that there was a fatal error. Something went wrong. In this case, the file did not exist, and the program quit. Check for typos.

---

### Post by coolbeans777 on 2011-02-21
Also, i just realized you typed "tar xzpf" try it without the p 
Eg (tar xzf)

---

### Post by dcstar on 2011-02-22
> **dderolph said:**
> I'm running Ubuntu 10.04LTS as a virtual machine using VMware Player. I want to use Terminal to use tar to install VMware Tools for VMware Player per instructions at [http://www.vmware.com/support/ws55/d...html#wp1127214](http://www.vmware.com/support/ws55/d...html#wp1127214).  I'm getting the following error message. Can someone shed some light on this?


```
david@ubuntu:~$ sudo tar zxpf /mnt/cdrom/VMwareTools-8.4.5-324285.tar.gz
[sudo] password for david: 
tar: /mnt/cdrom/VMwareTools-8.4.5-324285.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
david@ubuntu:~$
```

```
ls -al /mnt/cdrom/VMwareTools-8.4.5-324285.tar.gz
ls -al /mnt/cdrom/
```

---

