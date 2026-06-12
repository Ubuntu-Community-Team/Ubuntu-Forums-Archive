---
title: "apt-get autoremove doesn't work well"
date: 2010-04-27
forum: General Help
---

### Post by megakilo on 2010-04-27
Hi,

I am running 10.04 and I used to run apt-get autoremove to remove the unneeded dependencies. But several times, I found autoremove doesn't find all the orphans.
Is this a bug of apt-get/aptitude?

E.g.
1. Install the **deborphan** package
_sudo apt-get install deborphan_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dialog
The following NEW packages will be installed:
  **deborphan dialog**
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2. Remove it
_sudo apt-get remove **deborphan**_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  deborphan
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 471kB disk space will be freed.

3. Try to autoremove the **dialog** package
_sudo apt-get autoremove_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Nothing found then. The **dialog** package is installed forever then.

---

### Post by mockingbird on 2010-04-27
> **megakilo said:**
> Hi,

I am running 10.04 and I used to run apt-get autoremove to remove the unneeded dependencies. But several times, I found autoremove doesn't find all the orphans.
Is this a bug of apt-get/aptitude?
<snip>

Is dialog a recommended or a dependency?

Try "sudo apt-get install --no-install-recommended install deborphan"

---

### Post by megakilo on 2010-04-27
> **mockingbird said:**
> Is dialog a recommended or a dependency?

Try "sudo apt-get install --no-install-recommended install deborphan"

Thanks. This is the reaseon for deborphan example.

But last time I installed lxde and removed it later. The lxterminal is still installed. This is a dependency of lxde.

---

### Post by wwwolf on 2010-04-27
What about apt-get purge Package_file and then apt-get autoremove?

---

### Post by megakilo on 2010-04-27
> **wwwolf said:**
> What about apt-get purge Package_file and then apt-get autoremove?

Same as remove.

I turned off the recommends in /etc/apt/apt.conf.d/99synaptic
_1. Install lxde_
The following NEW packages will be installed:
  gpicview leafpad libmenu-cache1 libobparser21 libobrender21 lxappearance lxde lxde-common lxde-core lxde-icon-theme lxinput lxmenu-data lxpanel lxrandr lxsession lxsession-edit lxshortcut lxterminal obconf openbox pcmanfm xarchiver
0 upgraded, **22** newly installed, 0 to remove and 0 not upgraded.

_2. Remove/Purge lxde_
The following packages will be REMOVED:
  lxde*
0 upgraded, 0 newly installed, **1** to remove and 0 not upgraded.

_3. Autoremove_
The following packages will be REMOVED:
  gpicview leafpad libmenu-cache1 lxappearance lxde-common lxde-core lxde-icon-theme lxinput lxmenu-data lxpanel lxrandr lxsession-edit lxshortcut obconf pcmanfm xarchiver
0 upgraded, 0 newly installed, **16** to remove and 0 not upgraded.

---

### Post by mockingbird on 2010-04-27
I'm on Vista, but I'm going to log in to Lucid to see if it works for me.  Autoremove has always worked great.

---

### Post by mockingbird on 2010-04-27
I can confirm this is a problem with the deborphan package.

Usually autoremove works very well for me.

---

