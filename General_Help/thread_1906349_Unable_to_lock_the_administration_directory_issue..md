---
title: "Unable to lock the administration directory issue."
date: 2012-01-08
forum: General Help
---

### Post by Udagama on 2012-01-08
Hi!
I try to open Advanced settings using terminal. Then i received following error how do i fix it.

```

home@ubuntu:~$ sudo apt-get install gnome-tweak-tool
[sudo] password for home: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
home@ubuntu:~$ 


```

Thanks! :popcorn:

---

### Post by genti on 2012-01-08
Do you have Synaptic or update-manager doing something?

Does this return anything?
ps aux  | egrep -i 'apt|ftp|kpack|dpkg'  | less

---

### Post by bluexrider on 2012-01-08
> **Udagama said:**
> Hi!
I try to open Advanced settings using terminal. Then i received following error how do i fix it.

```

home@ubuntu:~$ sudo apt-get install gnome-tweak-tool
[sudo] password for home: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
home@ubuntu:~$ 


```Thanks! :popcorn:
this is the sign that more than one package manager is working at the same time

---

