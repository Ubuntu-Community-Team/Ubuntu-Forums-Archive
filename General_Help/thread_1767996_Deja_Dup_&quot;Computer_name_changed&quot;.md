---
title: "Deja Dup: &quot;Computer name changed&quot;"
date: 2011-05-26
forum: General Help
---

### Post by amalgamas on 2011-05-26
After having struggled with VPN connection for a few days, Deja Dup refuses to backup and gives following message:
[INDENT]The existing backup is of a computer named BF-HP, but the current computer's name is localhost6.localdomain6.  If this is unexpected, you should back up to a different location.
[/INDENT]I messed with VPN-connection settings in the network manager, and I tried a program called KVpnc.

My /etc/hostname-file simply contains the correct computer name (BF-HP).
The /etc/hosts-file:
[INDENT]127.0.0.1    localhost
127.0.1.1    BF-HP

# The following lines are desirable for IPv6 capable hosts
::1     BF-HP ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
[/INDENT]After some googling I edited line ::1 and added BF-HP.  This didn't help

So where does this localhost6.localdomain6-thing come from?

---

### Post by alanchambers on 2011-10-28
Hi - I see your question has gone unanswered so I wonder if you found a solution to this? 

I have exactly the same thing - using the backup utility in Ubuntu 11.10.  It was working fine for a few days and now everytime it starts it gives the message you got.  Interestingly, it gives the same computer name localhost6.locadomain6, which I don't recognise as anything I've defined anywhere.

On the pop-up message, I can click "Continue" and it goes ahead fine but I've set scheduled backups and this message stops them happening unless I spot the problem, find the message and click "Continue".

---

