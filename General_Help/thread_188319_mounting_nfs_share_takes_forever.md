---
title: "mounting nfs share takes forever"
date: 2006-06-03
forum: General Help
---

### Post by nix4me on 2006-06-03
Any ideas why it takes 1 minute 45 seconds to mount a NFS share?

This should take 1 sec at most.

I've tried it several times and it always acts the same way.

nix4me

---

### Post by nix4me on 2006-06-03
Ok I fixed it.  I installed the portmap package on the client side and all is well.

I will be filing a bug against this.

nix4me

---

### Post by cambie on 2006-06-04
[QUOTE=nix4me]Ok I fixed it.  I installed the portmap package on the client side and all is well.

I will be filing a bug against this.

nix4me[/QUOTE]
why file a bug? portmap is just a package left out of the default install because it's figured it's not needed by all desktop users. If you need to mount an nfs share, then sudo apt-get install portmap and you're good to go. I had to do this too with 5.10, so it's not new with 6.06

---

### Post by professor_chaos on 2006-06-04
nfs-common depends on portmap.

---

### Post by loko on 2006-06-06
nix4me, thanks for the portmap-tip.

---

### Post by nix4me on 2006-06-08
no problem

---

### Post by alalbiol on 2006-10-16
I had the same problem, the solution is to install portmap:

sudo apt-get install portmap

And start this service: /etc/init.d/portmap start

(check that the system restarts when your computer boots in your runlevel)

After that mounting should be very fast

---

