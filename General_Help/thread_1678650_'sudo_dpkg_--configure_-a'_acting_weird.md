---
title: "'sudo dpkg --configure -a' acting weird"
date: 2011-01-30
forum: General Help
---

### Post by supermooshman on 2011-01-30
Hi all,

I recently (fifteen minutes ago) started my old desktop again and tried to do an update```
sudo apt-get update
```
Which gives me:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

When I try this, my screen goes back and after a few seconds I end up back at the loginscreen (I not logged in anymore)

The output of ```
sudo dpkg --configure -a
```is following
```
Setting up ubudsl (1.0.0.77-7) ...
 System start/stop links for /etc/init.d/ubudsld already exist.
Stopping UbuDSL daemon...
No /usr/sbin/ubudsldaemon found running; none killed.
```

anyone an idea what went wrong (and how to solve it)

Thanks

---

### Post by garvinrick4 on 2011-01-30
I do believe that your upgrades were stopped after downloaded and in the middle
of dpkg so your machine wants to finish its upgrade.
What does 
```
sudo apt-get -f install 

```
The command you already gave is right I will bump up to front to get others to
take a peak at this thread hopefully.

---

### Post by supermooshman on 2011-01-30
> **garvinrick4 said:**
> I do believe that your upgrades were stopped after downloaded and in the middle
of dpkg so your machine wants to finish its upgrade.
What does 
```
sudo apt-get -f install 

```The command you already gave is right I will bump up to front to get others to
take a peak at this thread hopefully.

thanks but unfortunately the output stays```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

any other advise?

---

### Post by derklempner on 2011-01-30
Check to see if there are any files in **/var/lib/dpkg/updates**. If there are files in that directory, delete them all and then run:
```
sudo apt-get update && sudo apt-get upgrade
```

---

