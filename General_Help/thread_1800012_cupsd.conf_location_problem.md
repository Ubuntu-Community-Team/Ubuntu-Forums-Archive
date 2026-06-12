---
title: "cupsd.conf location problem"
date: 2011-07-08
forum: General Help
---

### Post by J&#7885;hn on 2011-07-08
Hi all,

I've got a Lucid machine here running fine, if I move the cups directory out of /etc and onto an NFS mount, then softlink the cups new location into /etc, cups won't start. It complains about not being able to read the config file, all the permissions are correct afaics and if I login as the lp user I can read the files from nfs.

If I move it back again it works. Smells like a permissions problem but I'm overlooking something here.

```

cd /nfs
mv /etc/cups .
cd /etc
ln -s /nfs/cups cups
/etc/init.d/cups restart
```

Anyone have any idea what I could be missing?

Thanks

---

