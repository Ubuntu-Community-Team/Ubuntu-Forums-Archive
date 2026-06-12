---
title: "Interupted update"
date: 2012-06-06
forum: General Help
---

### Post by mksarath on 2012-06-06
Hi, i triend to update ubuntu 10.04. But the system was powered off in the middle. When i booted it again, many of the softwares like update-manager, software sources... etc are not opening up. Also i cant shutdown, it just go to the log in screen.

---

### Post by cariboo on 2012-06-07
Once you are at your desktop again, open a terminal and type the following command:

```
sudo apt-get -f install
```

This should start downloading and installing any missing packages. Next to make sure you are fully up to date, in the same terminal type:

```
sudo apt-get update && sudo apt-get upgrade
```

---

