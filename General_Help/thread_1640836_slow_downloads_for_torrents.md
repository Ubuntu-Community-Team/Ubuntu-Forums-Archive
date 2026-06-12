---
title: "slow downloads for torrents"
date: 2010-12-08
forum: General Help
---

### Post by mykb on 2010-12-08
Hello!

I'm facing slow download speeds in my torrent client, transmission. I've opened the ports in iptables however the client reports the port as closed.

Any ideas, ?

---

### Post by mykb on 2010-12-08
I opened the ports by:
sudo iptables -A INPUT -p tcp --dport 41715 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 41715 -j ACCEPT

---

