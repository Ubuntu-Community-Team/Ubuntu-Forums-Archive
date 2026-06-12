---
title: "How do i remove this folder?"
date: 2011-04-04
forum: General Help
---

### Post by Smaug95swe on 2011-04-04
I need to remove a folder. /var/cache/sandboxgamemaker    <-- That one
I know i cant do it just by going in there and delete it can someone paste the code so i can learn it? and use it?

---

### Post by matt_symes on 2011-04-04
Hi

> **Smaug95swe said:**
> I need to remove a folder. /var/cache/sandboxgamemaker    <-- That one
I know i cant do it just by going in there and delete it can someone paste the code so i can learn it? and use it?

Open a terminal and type

```
sudo rm -rf /var/cache/sandboxgamemaker
```

Enter your password. It will not be echoed to the screen.

You can also use Nautilus. Press ALT + F2 and type

```
gksudo nautilus
```

into the run dialog. Navigate to the folder and delete it. Then close Nautilus.

Kind regards

---

### Post by Smaug95swe on 2011-04-05
Thanks worked excellent i will not forget it :KS

---

