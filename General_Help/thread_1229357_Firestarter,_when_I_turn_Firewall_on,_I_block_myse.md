---
title: "Firestarter, when I turn Firewall on, I block myself from Internet access"
date: 2009-08-02
forum: General Help
---

### Post by ade234uk on 2009-08-02
I don't know how I managed to do this, but when I turn on Firestarter firewall I seem to have managed to block myself. 

Any ideas how to sort this one?

---

### Post by credobyte on 2009-08-02
Show us the output of:
```
sudo iptables -L

```

---

### Post by ade234uk on 2009-08-02
Here is the output:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by credobyte on 2009-08-02
Something else should be wrong with your installation/OS - iptables are empty which means that it can't be firestarters fault :roll:

---

### Post by Soul-Sing on 2009-08-02
> **ade234uk said:**
> I don't know how I managed to do this, but when I turn on Firestarter firewall I seem to have managed to block myself. 

Any ideas how to sort this one?

Please try to uninstall firestarter via synaptic packagemanager.
Try (if nec.) GUFW as a frontend for iptables.
- do you have still connection problems?
- what is the outcome of ```
sudo iptables -L
``` after installing GUFW?

---

### Post by ade234uk on 2009-08-02
Ok I removed Firestarter completely and I can now access pages through Firefox.

I also installed gufw, and enabled the firewall and can access pages through Firefox again.

Running the command iptables -L gives me the following output:
Looks like my machine is back to normal again.

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination

---

### Post by Soul-Sing on 2009-08-02
Seems ok. :D

---

