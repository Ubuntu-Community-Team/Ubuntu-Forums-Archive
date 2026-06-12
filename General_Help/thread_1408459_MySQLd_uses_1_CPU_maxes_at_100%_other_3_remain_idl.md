---
title: "MySQLd uses 1 CPU maxes at 100% other 3 remain idle"
date: 2010-02-16
forum: General Help
---

### Post by fierobuff on 2010-02-16
I am running Ubuntu server 2.6.31-14-generic-pae.  I am having an issue when I run MySQL. When I import the data from our MySQL database into our Excel spreadsheet using the OCDB connector, my CPU processor percentage maxes out to 100 percent until it finishes the process.  During this time we are unable to do anything else in MySQL.

This instance of Ubuntu is running on an ESXi server with 4 processors.  When I run a top, I am able to see all 4 processors however only 1 ever shows any activity.  The remaining three show 100 percent idle. I also ran cat \proc\cpuinfo and there are 4 processors listed.

Does anyone know how I can get my other processors to kick in?  They are not sharing the load at all.

Thank you

---

### Post by rnerwein on 2010-02-16
hi
the first is why can't you do anything else in MySQL during the import. i guess the database is locked.
the second. there is no more load on the box. but you can do anything else without MySQL. that's ok.
the job wich is running is sitting on one cpu and thats not bad because there are no inline cache fault when switching the cpu. also the process you run must have the ability to be multi threaded.
ciao

---

### Post by fierobuff on 2010-02-16
No other applications are involved.  MySQL is being called by the MySQL OCDB connector (written by mysql development).  How can I get it to use more than one processor?

---

### Post by Fire_Chief on 2010-02-16
Ok, we need to get some more specifics here as your description is a bit unclear...

You have a server with ESXi installed as the base. Check.
-Are you using the free version of ESXi?
-How many physical CPUs and Cores per CPU does the ESXi host have?

You have one VM setup on the ESXi host with Ubuntu installed. Check.
-Did you configure the VM to have multiple vCPUs or just 1?(can go up to 4)
-Have you verified that the Ubuntu kernel has SMP enabled? (probably true but doesn't hurt to check)

I'll keep thinking on it...

Cheers!

---

### Post by fierobuff on 2010-02-16
Sorry I was unclear.  Hopefully this will clear it up.

I am running on the free version of ESXi at the base.  The base host has two quad core Xeon processors.  

I configured the virtual machine to have 4 vCPUs.

I believe that SMP is enabled because when I run cat /proc/cpuinfo it shows 4 processors.

Thank you in advance for the help

---

### Post by Fire_Chief on 2010-02-17
Do you know if you configured any CPU Affinity in the VM settings?

---

