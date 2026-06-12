---
title: "spc and tar using own cpu power to tar"
date: 2011-02-13
forum: General Help
---

### Post by daxbau on 2011-02-13
Hello everyone!

I'd like to copy via scp data from an external host to local but also wanna archive the incoming data to a tar archive without compression. (The incoming data has virus's but needed)

the connection is local but via wireless.

can i do

```
scp root@192.168.1.1:/mnt/sda5/backup ~/backup | tar -cvf
```i don't think that that will do that.

can you help me?

---

### Post by shoot2kill on 2011-02-13
Im guessing you want to archive before you copy, to stop the virus spreading to your local machine?

Is ssh not available, so you can ssh into the remote machine and tar the file, then scp it?

also, the title for this thread is spc, not scp, which could be causing people not to view it as they dont know what spc is.

---

### Post by daxbau on 2011-02-14
thanks for the title hint ;)

no actually i wanna tar it with my local dualcore and not with the remote k7 800 MHz (ssh uses all for the tunnel :D )

```
ssh -n 192.168.1.2 "tar cvf - /mnt/sda5" | cat > /mnt/backup/remotehost_sda5.tar
``` would for example do what you suggested.

****[COLOR=Black]
[/COLOR]

---

