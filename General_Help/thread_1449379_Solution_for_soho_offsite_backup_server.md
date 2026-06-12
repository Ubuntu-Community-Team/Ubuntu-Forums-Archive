---
title: "Solution for soho offsite backup server"
date: 2010-04-07
forum: General Help
---

### Post by FatkidNtraining on 2010-04-07
I would like to make a server in my home that could be used to backup old job files at a print shop that I work at, creating a low cost offsite backup for our backup server. It would only backup 30-200mb a night, depending on what size the various jobs are.

There are 4 workstations that backup to a network share hosted on a fileserver(tower). It only has a single TB drive, and now people are offloading files to this server to free there computer of disk space. This is going to be a problem once the "server" disk fails. The managment there will not pay a monthly fee for 500+GB of files we prob will never need, but cant delete. I was hoping I could create some sort of "online" backup hosted at my house. ( like amazon, carbonite but without the fancy gui)

After researching a while I can't seem to come up with a great solution (partly due to my lack of networking knowledge i'm sure!). I have a pfSense router, with VPN capabilities, and the router at work (Cisco/Linksys RVS4000) also can VPN. I would like to use linux as the server, I am in the process of learning Ubuntu. Also freeNAS via FTP is another thought, might be easier?

Any ideas to point me in the right direction are **much **appreciated!! :)

---

### Post by dcstar on 2010-04-07
> **FatkidNtraining said:**
> I would like to make a server in my home that could be used to backup old job files at a print shop that I work at, creating a low cost offsite backup for our backup server. It would only backup 30-200mb a night, depending on what size the various jobs are.

There are 4 workstations that backup to a network share hosted on a fileserver(tower). It only has a single TB drive, and now people are offloading files to this server to free there computer of disk space. This is going to be a problem once the "server" disk fails. The managment there will not pay a monthly fee for 500+GB of files we prob will never need, but cant delete. I was hoping I could create some sort of "online" backup hosted at my house. ( like amazon, carbonite but without the fancy gui)

After researching a while I can't seem to come up with a great solution (partly due to my lack of networking knowledge i'm sure!). I have a pfSense router, with VPN capabilities, and the router at work (Cisco/Linksys RVS4000) also can VPN. I would like to use linux as the server, I am in the process of learning Ubuntu. Also freeNAS via FTP is another thought, might be easier?

Any ideas to point me in the right direction are **much **appreciated!! :)

People use rsync to backup to remote machines, you just need to configure secure access to the server to use it.

---

### Post by FatkidNtraining on 2010-04-08
Thanks David!

I will do some searching regarding Rsync :)

---

