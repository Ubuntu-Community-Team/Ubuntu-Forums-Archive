---
title: "PolicyKit Policies"
date: 2012-10-12
forum: General Help
---

### Post by demol1d0r on 2012-10-12
I messed up PolicyKit policies now I need to download them again to put on /usr/share/polkit-1/actions folder.

My "User Accounts" management thing is not opening anymore because of this.

Can anyone help me with this? tnks

---

### Post by Rexilion on 2012-10-13
```
for i in /usr/share/polkit-1/actions/*
          do dpkg -S $i
done
```

language-selector-common: /usr/share/polkit-1/actions/com.ubuntu.languageselector.policy
apt-xapian-index: /usr/share/polkit-1/actions/org.debian.aptxapianindex.policy
accountsservice: /usr/share/polkit-1/actions/org.freedesktop.accounts.policy
consolekit: /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
policykit-1: /usr/share/polkit-1/actions/org.freedesktop.policykit.policy
udisks: /usr/share/polkit-1/actions/org.freedesktop.udisks.policy
upower: /usr/share/polkit-1/actions/org.freedesktop.upower.policy
upower: /usr/share/polkit-1/actions/org.freedesktop.upower.qos.policy
xfce4-power-manager: /usr/share/polkit-1/actions/org.xfce.power.policy

```
aptitude reinstall language-selector-common apt-xapian-index accountsservice consolekit policykit-1 udisks upower xfce4-power-manager
```

OR, just be more specific and do only:

```
aptitude reinstall accountsservice
```

---

