---
title: "Is It Possible To Resume Upgrade?"
date: 2011-12-07
forum: General Help
---

### Post by tito-dutta on 2011-12-07
I started to upgrade to Ubuntu 11.10 [from 11.04), when the upgrading was almost complete, power cut off.
Is it possible to resume that previous upgrade?

---

### Post by BC59 on 2011-12-07
In what situation is your computer now?

It's working without problem?

You could run:

```
sudo dpkg --configure -a
sudo apt-get -f install
```

to ensure all necessary packages are completely installed and configured.

If everything looks working you could try again to resume the upgrade.

---

### Post by beew on 2011-12-07
Instead of resuming upgrade just abort the whole thing, back up your data and do a fresh install. A fresh install takes 20-30 mins and much less problem prone And now you already have a broken upgrade this make it even more problematic.

---

### Post by tito-dutta on 2011-12-07
I can not see any option to upgrade there (that option is not included)

Tell me if I manage to collect a CD of Ubuntu 11.10, can I upgrade from there?

---

### Post by beew on 2011-12-07
> **tito-dutta said:**
> I can not see any option to upgrade there (that option is not included)

Tell me if I manage to collect a CD of Ubuntu 11.10, can I upgrade from there?

You should save your data and do a clean install. Many people break their systems trying to upgrade (especially to 11.10, since it is very different from previous versions)

---

### Post by BC59 on 2011-12-07
Press Alt+F2, type update-manager -d into the box and click Run

---

### Post by tito-dutta on 2011-12-07
> **beew said:**
> You should save your data and do a clean install. Many people break their systems trying to upgrade (especially to 11.10, since it is very different from previous versions)
- Where shall I save 300 GB data? :-o
- Can I upgrade from a CD ISO file?

---

### Post by beew on 2011-12-07
> **tito-dutta said:**
> - Where shall I save 300 GB data? :-o
- Can I upgrade from a CD ISO file?
  Even if you upgrade you still should have backed up your data so the space should not be a problem at this point. ;)

---

### Post by tito-dutta on 2011-12-07
> **BC59 said:**
> Press Alt+F2, type update-manager -d into the box and click Run
: I am attaching a file.

---

### Post by BC59 on 2011-12-07
> **tito-dutta said:**
> : I am attaching a file.

The command from Alt+F2 is:

```
update-manager -d
```

---

### Post by tito-dutta on 2011-12-07
> **beew said:**
> Even if you upgrade you still should have backed up your data so the space should not be a problem at this point. ;)

:Thanks! Any **alternative** shipit is available currently? You know?

---

### Post by BC59 on 2011-12-07
In any case I agree with @deew. I was only answering to your question how to resume the upgrade. To avoid any problems it's easier and more efficient to do a fresh install.

In the future, during installation, create a separate ~/home partition to store your data and to avoid similar situations.

---

### Post by tito-dutta on 2011-12-07
> **BC59 said:**
> The command from Alt+F2 is:

```
update-manager -d
```
Thanks! I am being redirected to upgrade page [screenshot] where I think upgrading is starting from the beginning, if I try to close it, I am getting this option [highlighted in screenshot] Shall I go for partial upgrade?

---

### Post by BC59 on 2011-12-07
> **tito-dutta said:**
> Thanks! I am being redirected to upgrade page [screenshot] where I think upgrading is starting from the beginning, if I try to close it, I am getting this option [highlighted in screenshot] Shall I go for partial upgrade?

Yes do a partial upgrade.

---

