---
title: "Cannot Install Wine (Offline)"
date: 2012-05-22
forum: General Help
---

### Post by ProNux on 2012-05-22
I want to install the downloaded Wine 1.3.deb to Ubuntu 12.04 LTS, but the "install" button is not highlighted on the Ubuntu Software Center.  My Ubuntu is on Persistent Live USB.

For some reason, I cannot install Wine using the apt-get command since I do not have "YET" a working internet connection, so I downloaded Wine and want to install it offline.

Thanks for those who can advise.

---

### Post by idoitprone on 2012-05-22
> **ProNux said:**
> I want to install the downloaded Wine 1.3.deb to Ubuntu 12.04 LTS, but the "install" button is not highlighted on the Ubuntu Software Center.  My Ubuntu is on Persistent Live USB.

For some reason, I cannot install Wine using the apt-get command since I do not have "YET" a working internet connection, so I downloaded Wine and want to install it offline.

Thanks for those who can advise.

apt-get is only for repositors

dpkg is for packages
```
sudo dpkg -i packageName
```

---

### Post by ProNux on 2012-05-23
^^ Thanks bro, it worked.

---

