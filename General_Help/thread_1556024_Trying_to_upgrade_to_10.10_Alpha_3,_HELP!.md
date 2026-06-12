---
title: "Trying to upgrade to 10.10 Alpha 3, HELP!"
date: 2010-08-18
forum: General Help
---

### Post by samureptile on 2010-08-18
I tried accessing the update manage through the "Alt+F2" command box and entering "update-manager-d", but upon running, it reads

"Error stating file '/home/hannah/update-manager-d': No such file or directory"

I can access it through System>Administration>Update Manager, but, I haven't been able to update the package information for "87 days" and it doesn't say and upgrade is available.

---

### Post by jupitertsax on 2010-08-18
there is a space between manager and -d

---

### Post by xangua on 2010-08-18
not a good isea, is still alpha

---

### Post by sandyd on 2010-08-18
> **samureptile said:**
> I tried accessing the update manage through the "Alt+F2" command box and entering "update-manager-d", but upon running, it reads

"Error stating file '/home/hannah/update-manager-d': No such file or directory"

I can access it through System>Administration>Update Manager, but, I haven't been able to update the package information for "87 days" and it doesn't say and upgrade is available.
run this
```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by samureptile on 2010-08-19
Thanks, all. I'm still trying to figure this all out.

I have also had issues with my update manager, reading as:
Failed to fetch [http://ppa.launchpad.net/COMPUTOR/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/COMPUTOR/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found
 Failed to fetch [http://ppa.launchpad.net/pmcenerey/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/pmcenerey/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

so the package information hasn't update for nearly three months now. 

This should probably be posted in a new thread, but if anyone could help here, that would be great.

---

### Post by samureptile on 2010-08-19
> **jupitertsax said:**
> there is a space between manager and -d
Hmm, how dumb of me...

---

### Post by oldos2er on 2010-08-19
Disable the problematic PPAs in Software Sources, then you should be able to successfully run the commands carlee gave you.

10.10 should be used for testing purposes only.

---

### Post by supermario641996 on 2010-08-19
Are you puting it on your system becuase its not a good idea to use 10.10 on a machine yet.  Use it under VirtualBox.

---

### Post by psycho5 on 2010-08-19
Stay away from the alpha, beta release. If you do want to use it, as the guys said, just run it in virtual box. They are still in testing mode.

---

### Post by Mark Phelps on 2010-08-19
In future, please do NOT post questions about alphas, or betas, in this forum.  This forum is reserved for questions on Released versions of Ubuntu.

Please post your questions on versions still under development to the appropriate Development forum.

Thanks

---

