---
title: "MS remote desktop to virtual box XP"
date: 2010-06-12
forum: General Help
---

### Post by sam1948 on 2010-06-12
the web is fulled with knowledge but non of it worked for me.
in the settings of  a machine i don't have a remote tab to change.

I think there must be something i missing.

i tried 
"rdesktop virtual-machine-ip" (from ipconfig)
"rdesktop localhost" ('cause someone said)

the firewall in the virtual XP is disabled

one more thing i m trying to connect from local machine to the local virtual machine 

regards

---

### Post by prodigy_ on 2010-06-12
Try ```
telnet <your_VM_IP_address> 3389
``` command. What error message do you get?

---

### Post by Jeroensum on 2010-06-12
Did you enable remote desktop in the XP VM?

---

### Post by sam1948 on 2010-06-12
> :~$ telnet 10.0.2.15 3389
Trying 10.0.2.15...
telnet: Unable to connect to remote host: Connection timed out
remote desktop was enabled and an allowed user was selected.
:(

---

### Post by _Mark_ on 2010-06-12
What is your hosts IP address and what is your guest ip address?

My guess is they will be on different subnets, what network settings have you used on the VM if it NAT you won't be able to connect as they will be different ranges you need to setup as host interface ( i think that's what it's called haven't used v box for a while) so it will use the hosts network interface and be on the same subnet

---

### Post by John Bean on 2010-06-12
Can you "see" the VM on the network? The default network type won't work if you need to connect to a VM from the outside, you need to change it to ""Bridged" or "Host only" and restart your VM.

---

### Post by prodigy_ on 2010-06-12
> **sam1948 said:**
> telnet: Unable to connect to remote host: Connection timed out
This suggests a connectivity issue. Can you ping your VM from Ubuntu?

---

### Post by sam1948 on 2010-06-12
> **prodigy_ said:**
> This suggests a connectivity issue. Can you ping your VM from Ubuntu?

no ping.
i also installed a telnet server on the XP.
I **can** connect from the XP to itself but not from outside of it

---

### Post by sam1948 on 2010-06-12
> **John Bean said:**
> Can you "see" the VM on the network? The default network type won't work if you need to connect to a VM from the outside, you need to change it to ""Bridged" or "Host only" and restart your VM.

thanks John
 this what eventually worked 
- shutdown the virtual machine.
- open settings 
- in the network tab **set adapter to bridge**.

here is the catch:
i have an Internet without a dialer. there is some online loging in.
it is possible that ISP with dialer won't allow this type of access
(or even my provider if somehow he will find out) 
in that case the bridge will be have to be defined properly.
 
many thank to all of u

---

### Post by prodigy_ on 2010-06-13
You don't need telnet server to test ports with telnet. It's just a useful trick to see if anything is listening on a specific port (RDP is 3389) on the other end. ;-)

But if telnet just times out, it's a connection issue (no physical link, firewall, wrong TCP/IP settings, broken routing, etc.)

---

