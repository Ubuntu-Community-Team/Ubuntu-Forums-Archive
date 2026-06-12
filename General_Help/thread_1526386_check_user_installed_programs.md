---
title: "check user installed programs"
date: 2010-07-08
forum: General Help
---

### Post by COKEDUDE on 2010-07-08
How do check the programs that the actual user of the computer installed. I do not care at all about the default programs that came with your distro of Linux, I only want the user installed programs.

---

### Post by Gregorybekkers on 2010-07-08
all applications installed can u find in the Ubuntu software center under Installed applications.

---

### Post by COKEDUDE on 2010-07-09
> **Gregorybekkers said:**
> all applications installed can u find in the Ubuntu software center under Installed applications.

I'm using Mint. If Installed applications is anything like synaptic then it shows all the programs that came by default with your distro of Linux.

---

### Post by CannibalZerg on 2010-07-09
> **COKEDUDE said:**
> I'm using Mint. If Installed applications is anything like synaptic then it shows all the programs that came by default with your distro of Linux.
There is no simple solution for this task. You can parse dpkg.log, like:
```

[SIZE=3]zcat -f /var/log/dpkg.log* | grep "\ install\ " | sort[/SIZE]

```But, result of this command contains ALL installed packages. You can use additional filters by date, to exclude "default distro" packages. But most worst is that dpk.log entries has the same mark "installed" for updated packages too. So, I think you should write couple non trivial scripts: first of them should retrieve to some temp file package list, that was installed with distro. Something like: get the earliest date from dpkg.log* and make list of installed packages during that date (you will get the "default distro" pkg list).
The second script should parse the rest of logs and remove entries, that presents in temp file: in such way you exclude entries with updates for "default distro" packages.

---

