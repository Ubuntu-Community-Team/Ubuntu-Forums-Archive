---
title: "wine dependencies libfontconfig &amp; libgnutls26"
date: 2009-08-17
forum: General Help
---

### Post by labinnsw on 2009-08-17
I am getting the following error message when I try to install the latest version of wine as outlined in [this link]("http://www.winehq.org/download/deb")

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libfontconfig but it is not installable
        Depends: libgnutls26 but it is not installable
E: Broken packages
```

I checked synaptic.

No broken packages are listed.
libfontconfig1 is installed.
libgnutls26 is not listed
libgnutls13 is installed

If I am not making any sense, please pardon my ignorance and help anyway. Your assistance will be tremendously appreciated.

---

### Post by nikhilk on 2009-08-17
> **labinnsw said:**
> I checked synaptic.

No broken packages are listed.
libfontconfig1 is installed.
libgnutls26 is not listed
libgnutls13 is installed

If I am not making any sense, please pardon my ignorance and help anyway. Your assistance will be tremendously appreciated.

Could you double check if you have added the correct Wine repository for Hardy Heron? I say that because libgnutls26 package is available for Interprid and Jaunty only (both higher versions than the Hardy that you are using).

This is the repository for Hardy as listed on the Wine site
> deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"

---

### Post by labinnsw on 2009-08-17
Just to make sure, except for getting the key, I did the entire process over again.(I used the command line)

The complete output is attached.

[ATTACH]125227[/ATTACH]

---

### Post by nikhilk on 2009-08-18
I am not able to confirm this as I am not near my Ubuntu box but might be packaging error from the Wine team as the latest version is still in beta phase.

Can you install an older, stable version and see if that goes OK?

---

### Post by labinnsw on 2009-08-19
I know the older version works because I had it installed from the repositories and it was working. It did not run many applications which others are reporting should work. I tried the latest version on a partition I use for testing and some of those applications worked. Now I am trying to install it on my default partition.

I don't think the problem is wine. It might be that something moved or changed in my system over time. In other words, I might need some sym-links.

---

