---
title: "Need some help on scripting"
date: 2012-05-17
forum: General Help
---

### Post by Tolein on 2012-05-17
I have a server at my home which I transfer files to and from while at work via scp. This is what I am wanting to accomplish. I would like for the system to look in my specified directories on my laptop and then compare the directories on my server. If the files do not exist, then copy them to the server but if they do exist then do nothing. I do not believe an scp option will accomplish this. I am looking for advice on how to accomplish this. Thanks

---

### Post by Zulu-Zeffir on 2012-05-17
Why not try something like dropbox instead?

---

### Post by Cheesemill on 2012-05-17
Use rsync.
```
man rsync
```

---

### Post by matt_symes on 2012-05-17
Hi


> **Cheesemill said:**
> Use rsync.
```
man rsync
```

over an ssh tunnel.


Kind regards

---

### Post by Tolein on 2012-05-17
Thanks for the replies. I'm working on using rsync and I feel that I am almost there but for some reason it will not copy to my server. I can however copy from my server. This is what I am typing to copy to my server.

rsync -avze "ssh -p 12345" /home/myself/testdir/ username@123.45.67.89:/home/myself/testdir

I get a message that says sending incremental file list but nothing copies to my server. If however I reverse the source and destination it will copy files to my laptop. Any ideas?

---

### Post by matt_symes on 2012-05-18
Hi

Check each part individually.

Can you ssh from the client to the server ?
Can you rsync from the client to the server without ssh ?

Your ssh keys are set up correctly ?

Are you trying this over your LAN or from work ?

Its difficult to advise without knowing what you have tried.

Kind regards

---

### Post by Tolein on 2012-05-18
I was able to get it setup properly today. I had ssh with key authentication already setup so that wasn't the issue. Also commenting on the post above, dropbox would not work for me because I am transferring large amounts of data and need a secure connection. Rsync was just the ticket. This is the command of how I got it to work.

rsync -avze 'ssh -p port_number' /source_path/ shane@ipaddress:/destination_path/

Thanks again

---

