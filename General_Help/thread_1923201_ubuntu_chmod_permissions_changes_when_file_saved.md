---
title: "ubuntu chmod permissions changes when file saved"
date: 2012-02-10
forum: General Help
---

### Post by danny620 on 2012-02-10
Hi, ive set up samba file share "northplanet"

I have a group "web-designers" with two users in it "danny","chris"

now i did have problems with chris being able to create folders in "northplanet" so i changed the folder chmod 770 to enable the group "web-designers" to be able to write

however when i open a file with 770 on it and then resave it the chmod permissions are changed to 750 how can i stop this from happening as its cause issues with the group being able to not edit the file?

---

### Post by Khayyam on 2012-02-10
danny620 ..

I'm not a Samba admin but I do play one on TV.

That said, I'm pretty sure that these are set via smb.conf. These values do not override filesystem permissions and so they need to be set to allow 'webdesigners' to write, but that seems to be taken care of.

The following section of smb.conf should get a 0770 mask.

```
[webdesigners]
path = /path/to/northplanet
write list = danny chris
writeable = Yes
create mask = 0770
```

Again, I've not much experience with samba but this should work as advertised.

HTH ..

---

