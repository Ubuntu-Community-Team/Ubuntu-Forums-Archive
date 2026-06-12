---
title: "generating a list of installed apps"
date: 2010-12-05
forum: General Help
---

### Post by rmcellig on 2010-12-05
How can I generate a list of all the apps I have installed in my Ubuntu installation?

---

### Post by Verbeck on 2010-12-05
dpkg --get-selections > list-of-installed-software

it'll include everything though, not only user installed programs

---

### Post by sisco311 on 2010-12-05
System -> Administration -> Synaptic Package Manager -> File menu -> Save Markings As... -> Select *Save ful state, not only changes*

---

### Post by ajgreeny on 2010-12-05
If you have always used synaptic to install packages you can use the following:-
```
sudo -i
cd /root/.synaptic/log
cat /root/.synaptic/log/*.log > /home/*username*/dpkg-$(date +%F).log
```

Will produce file called dpkg-2010-12-05.log (dpkg-year-month-day.log)

It may work if you use USC, but I don't use it, so I'm not sure.

---

