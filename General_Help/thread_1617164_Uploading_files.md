---
title: "Uploading files"
date: 2010-11-09
forum: General Help
---

### Post by Drenriza on 2010-11-09
On a regular basics i need to upload big files 4,5 - 6GB. On unstable or slow Ethernet connections.

And I'm wondering, is their a way via the Linux CLI to upload a file. And if the connection should crash, once it is restored (again) the file can continue to upload from where it last stopped? It would need to be a secure (encrypted) connection.

Do i need to install some sort of program on sender and receiver? to keep track of this.

I would like to say that the receivers are an Linux server edition and their fore does not have a GUI. 

Thanks on advance.
Kind Regards

---

### Post by Drenriza on 2010-11-09
solved. ended up with

rsync -a -r -z -v --progress --partial -e ssh /source user@destination:/destination

---

