---
title: "Everything freeze when cifs or smbfs drive becomes unreachable"
date: 2011-08-09
forum: General Help
---

### Post by PaNtHeR on 2011-08-09
Hi, 

I have Ubuntu machine with cifs share mounted at boot via /etc/fstab

fstab entry looks like this:
/kain/buksica   /media/buksica   smbfs owner,_netdev,gid=xxxx,uid=xxxxx   0 0

When my coleague shuts down his windblows machine my Ubuntu box freezes.. I cannot even open my home folder.

Is there any way kernel can detect that this share is down and silently umount it or in some other way keep stable.

TNX!

---

### Post by blind2314 on 2011-08-09
> **PaNtHeR said:**
> Hi, 

I have Ubuntu machine with cifs share mounted at boot via /etc/fstab

fstab entry looks like this:
/kain/buksica   /media/buksica   smbfs owner,_netdev,gid=xxxx,uid=xxxxx   0 0

When my coleague shuts down his windblows machine my Ubuntu box freezes.. I cannot even open my home folder.

Is there any way kernel can detect that this share is down and silently umount it or in some other way keep stable.

TNX!

Try adding the "soft" argument to your fstab entry. That will make the kernel disregard the mount if it hangs, and return the errors to the client that was using the share (your friend), rather than the server (you).

---

### Post by PaNtHeR on 2011-08-10
Tnx for the hint but "soft" hasn't helped anything... I also tried smbfs and cifs mounts but my Ubuntu box still hangs after Win machine is turned off or I unplug LAN cable.

Anything else I could try?

@blind Also I think you might got it wrong. Windows machine is the server in this case... the share /kain/buksica is at Windows machine. Just to clarify.

---

### Post by Mark Phelps on 2011-08-10
I ran into the very same problem -- which is why I took it OUT of my FSTAB and created a script to do the mount upon demand.  Little more work, but it prevented the PC from hanging when the Windows PC was turned off.

---

### Post by PaNtHeR on 2011-08-10
Sonuds OK to me... could you please post this script so I can do the same.

Tnx.

---

### Post by HermanAB on 2011-08-10
The script will be something like this, which you can put in /usr/local/bin:

```
#/bin/bash
mkdir /mnt/wherever
mount -t cifs 1.2.3.4:/share /mnt/wherever
```

---

### Post by PaNtHeR on 2011-08-10
Tnx for your answer but even when I mount this share via mount -t I get the very same problem - if for any reason share stops responding my Ubuntu box become unusable.

Very strange that a network OS like this can't get this right, I mean it's some basic stuff.

---

