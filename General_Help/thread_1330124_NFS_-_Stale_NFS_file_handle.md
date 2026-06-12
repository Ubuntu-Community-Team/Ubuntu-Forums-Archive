---
title: "NFS - Stale NFS file handle"
date: 2009-11-18
forum: General Help
---

### Post by ^_Pepe_^ on 2009-11-18
Hi all!

After updating to 9.10, now, my network NFS connection tends to fail (not always).

NFS server is a 9.10 machine with a 1TB HDD, and NFS server.
NFS clients are a couple of laptops (WiFi connected). One with 9.04 and other with 9.10. NFS connection is included on /etc/fstab with defaults. 

Sometimes, connection works at startup, sometimes not. When OK, after a time, files "dissapear" from Nautilus, and 

```
ls /media/TERA 
```

gives me 

Stale NFS file handle, but I can still see the folders.

In any case, unmount and remount commands solve the problem, but temporarilly.

Any ideas?

I only could find in Google some advice to unmont and mount again. (Not valid for me)

Here I found some information [http://systemadmin.es/2008/11/como-corregir-los-errores-stale-nfs-file-handle](http://systemadmin.es/2008/11/como-corregir-los-errores-stale-nfs-file-handle) to include some commands in Server ¿is it? It's Spanish (my language) so I can translate if needed.

Thanks for helping!

^_Pepe_^

---

