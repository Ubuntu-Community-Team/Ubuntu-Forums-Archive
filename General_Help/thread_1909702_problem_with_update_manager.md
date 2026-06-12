---
title: "problem with update manager"
date: 2012-01-15
forum: General Help
---

### Post by solitario on 2012-01-15
Hello folks.
I've had this thing in my Update Manager which just will not go away. The checkbox to the left of the option will not check. As if it is disabled. Screenshot attached.
Any help is appreicated.
Thanks.

---

### Post by Q-collective on 2012-01-15
It probably is a package that will only be upgraded via a system-upgrade. The easiest and best solution is to upgrade to Ubuntu 11.10. Be sure to have a backup before you do anything of course.

---

### Post by bluexrider on 2012-01-15
Try using terminal

```
sudo apt-get update && sudo apt-get upgrade
```

if you want system upgrades then

```
sudo apt-get dist-upgrade
```

---

### Post by Q-collective on 2012-01-15
> **bluexrider said:**
> Try using terminal

```
sudo apt-get update && sudo apt-get upgrade
```

if you want system upgrades then

```
sudo apt-get dist-upgrade
```

Mind that the latter command will also upgrade you to 11.10.

---

### Post by bluexrider on 2012-01-15
I think not sir, that code is used for distribution upgrades. 

if this were done then it would be a release upgrade
```

sudo do-release-upgrade -d
```

---

### Post by Q-collective on 2012-01-15
> **bluexrider said:**
> I think not sir, that code is used for distribution upgrades. 

if this were done then it would be a release upgrade
```

sudo do-release-upgrade -d
```

Hmm, you are correct.

So, to the OP: Post 3 offers the way to solve this issue :)

---

