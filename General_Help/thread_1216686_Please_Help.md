---
title: "Please Help"
date: 2009-07-18
forum: General Help
---

### Post by WLRR on 2009-07-18
Please help, I am new with ubuntu and would like to know if it has a firewall and virus control installed.
Will Ramage

---

### Post by c0mput3r_n3rD on 2009-07-18
> **WLRR said:**
> Please help, I am new with ubuntu and would like to know if it has a firewall and virus control installed.
Will Ramage

Install firestarter firewall from the add/remove programs.  And they have anti-virus as well, how ever this is not Winblows and you will be fine with out one.

---

### Post by WLRR on 2009-07-18
> **c0mput3r_n3rD said:**
> Install firestarter firewall from the add/remove programs.  And they have anti-virus as well, how ever this is not Winblows and you will be fine with out one.

Firestarter is not in the list on add/remove index. I have searched for it to no avail.

---

### Post by c0mput3r_n3rD on 2009-07-18
```

sudo apt-get install firestarter

```
In terminal

---

### Post by ibutho on 2009-07-18
Ubuntu like most Linux distros comes with a builtin firewall called netfilter/iptables. Firestarter is one of many frontends to the firewall. In Ubuntu, to manage the firewall, look at ufw (command line tool) and gufw (GUI labeled as "Firewall Configuration" in the System menu). These two apps are installed by default.

---

