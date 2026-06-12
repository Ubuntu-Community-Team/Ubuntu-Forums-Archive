---
title: "How to install package from Quantal into Precise"
date: 2012-08-28
forum: General Help
---

### Post by TristanSt on 2012-08-28
Hello,
Due to a specific bug in modem-manager that I'm stumbling upon I've been encouraged to update the version of MM that I'm running to the one at [https://launchpad.net/ubuntu/quantal/amd64/modemmanager](https://launchpad.net/ubuntu/quantal/amd64/modemmanager). I've tried downloading the .deb file but Software Centre then tells me that Modem-manager is already up to date.

Can anybody help me to get this new version installed?

Thanks

---

### Post by MG&amp;TL on 2012-08-28
Bear in mind that this will probably break things. Quantal itself is relatively stable, but mixing packages....not sure about that.

Anyway, if software centre is refusing, open up a terminal and do the following, assuming that your file is in Downloads/modemmanager.deb:

```
sudo dpkg -i ~/Downloads/modemmanager.deb
```

which should manually unpack the package.

---

### Post by TristanSt on 2012-08-28
The dependencies are pretty limited.
Thanks for the reply, dpkg did the trick, although I actually suspect that Software Centre was working fine - I just wasn't expecting /usr/sbin/modem-manager to show a modified time of June 2012 - this of course was the timestamp of when the package was created.

Many thanks

---

