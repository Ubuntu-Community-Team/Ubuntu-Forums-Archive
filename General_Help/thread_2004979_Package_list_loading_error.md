---
title: "Package list loading error"
date: 2012-06-16
forum: General Help
---

### Post by Tornikee on 2012-06-16
Could somebody tell me what this error is about and how I should solve it?

[http://bit.ly/N30n73](http://bit.ly/N30n73)

Cheers in advance.

---

### Post by drs305 on 2012-06-16
These commands should clear the lists and redownload them. Bevery careful with the command, as a typo and extra space could erase important system files.

```
sudo rm -vf /var/lib/apt/lists/* && sudo apt-get clean  && sudo apt-get update
```

---

### Post by drs305 on 2012-06-16
These commands should clear the lists and redownload them:

```
sudo rm -vf /var/lib/apt/lists/* && sudo apt-get clean  && sudo apt-get update
```

If it doesn't solve things, run this variation to remove the contents of /var/lib/apt/lists/partial:

```
sudo rm -vf /var/lib/apt/lists/partial/* && sudo apt-get clean  && sudo apt-get update
```

---

### Post by Tornikee on 2012-06-17
The first one solved it. Thanks a lot.

---

