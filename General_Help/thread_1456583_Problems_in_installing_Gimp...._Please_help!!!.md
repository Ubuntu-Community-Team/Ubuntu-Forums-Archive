---
title: "Problems in installing Gimp.... Please help!!!"
date: 2010-04-17
forum: General Help
---

### Post by chris.jericho on 2010-04-17
Hey there....

I want to install Gimp in my Ubuntu machine... running the latest version of Ubuntu -- the 10.04 lucid lynx beta 2....

so I typed in ```
apt-get install gimp
```

but soon after I get this error message....

```

chris@chris-desktop:~$ apt-get install gimp
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
chris@chris-desktop:~$ 

```

Please help!!!
I've install Filezilla before using the same kind of code and it was successful.... can't understand whats the problem here.... !!

Please help me out on this....!!!

---

### Post by howefield on 2010-04-17
Try typing

```
sudo apt-get install gimp
```

---

### Post by chris.jericho on 2010-04-17
hey thanks a lot bro...... the sudo thing worked.... :) :)

---

### Post by howefield on 2010-04-17
> **chris.jericho said:**
> hey thanks a lot bro...... the sudo thing worked.... :) :)

Imagine that !!

Glad you're sorted :)

---

