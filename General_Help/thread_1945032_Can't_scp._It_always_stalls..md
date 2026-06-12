---
title: "Can't scp. It always stalls."
date: 2012-03-22
forum: General Help
---

### Post by Grumpyo on 2012-03-22
Hi,

I have some remote servers that I need to be able to access from home. I can ssh into them without any problem but I can't scp. 

When I scp it just stalls indefinitely. 
What's really weird is that I can scp no problem from that server to my local computer. 

I really don't know where this could come from. I have just installed xubuntu 11.10 so I'm wondering if there is something that I should enable or change? Or could the problem come from my router??

Thanks for the help

---

### Post by letoasty on 2012-03-22
Where are the local machines? It is very likely that you need to set up port 22 routing to them on their local router (if they are not a rented server in the cloud). If there is indefinite stalling, a port routing issue would be my first guess. Otherwise, there may be a known_hosts/authenticated_hosts failure on the remote machine that is refusing your key due to suspicious access. That issue could be resolved by deleting your known_hosts file in ~/.ssh/ on the remote machine.

---

### Post by ksa618 on 2012-03-22
Sounds weird. What does scp print if you run it with the -v switch?

---

