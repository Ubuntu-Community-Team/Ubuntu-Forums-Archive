---
title: "Cant install ssh on 10.10"
date: 2011-06-26
forum: General Help
---

### Post by Scorpuk on 2011-06-26
When I try to install ssh I get the attached error messages.


Any help?

---

### Post by crispy_420 on 2011-06-26
sudo apt-get install -f

or in synaptic: Edit -> "fix broken packages"

---

### Post by Scorpuk on 2011-06-26
ok tried that, but get no further:

```

john@john-Aspire-R3610:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@john-Aspire-R3610:~$ sudo apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 ssh : Depends: openssh-server but it is not going to be installed
E: Broken packages
john@john-Aspire-R3610:~$ 
```

---

### Post by Toz on 2011-06-26
If you are trying to re-install the ssh program (which I believe is installed by default on ubuntu), try installing **openssh-client** instead. If you want the server component, try installing **openssh-server**.

---

### Post by gmargo on 2011-06-26
It is because your system is out of date.
Please do an "apt-get update ; apt-get dist-upgrade", then try the install again.

---

### Post by tredegar on 2011-06-26
> Please do an "apt-get update ; apt-get dist-upgrade", then try the install again.
Be warned: **apt-get dist-upgrade** will leave you with ubuntu 11.04. You may not want that.
An **apt-get update** will probably allow you to execute **apt-get install openssh-server** successfully.

---

### Post by gmargo on 2011-06-26
> **tredegar said:**
> Be warned: **apt-get dist-upgrade** will leave you with ubuntu 11.04. 

That is not correct.  "apt-get dist-upgrade" performs the same function as "apt-get upgrade" plus additional "smart" conflict resolution in case some packages need to be removed.

But I understand the confusion.

In the olden days (when I had to hike uphill both ways to work), in order to do a release upgrade, we would manually edit the **sources.list(5)** file, and use "apt-get update; apt-get dist-upgrade".  And it usually worked.  These days, it is recommended that you use **do-release-upgrade** to do a release upgrade.

**apt-get(8)** by itself will _never_ edit the **sources.list(5)** files that control which repositories are used.  Hence it is quite safe to use the dist-upgrade command.

Besides, everyone always runs apt-get with the "-s" option first, right?  

```

-s, --simulate, --just-print, --dry-run, --recon, --no-act
No action; perform a simulation of events that would occur but do not actually change the system.

```

---

### Post by tredegar on 2011-06-27
gmargo,
Thanks for clarifying that. I learn something new all the time.

---

### Post by Scorpuk on 2011-06-29
Thank you very much.


It worked a treat. :-)

---

