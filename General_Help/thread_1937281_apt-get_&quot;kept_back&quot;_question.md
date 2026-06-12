---
title: "apt-get &quot;kept back&quot; question"
date: 2012-03-07
forum: General Help
---

### Post by teejay17 on 2012-03-07
Why are some of my packages (Chromium, Linux Kernel, etc.) "kept back" when using apt-get update, but when I do an "aptitude" update, all the packages, including the the "kept back" ones, are installed?

---

### Post by CharlesA on 2012-03-07
upgrade only updates packages and doesn't install new ones. You can use dist-upgrade to install the new packages.

---

### Post by teejay17 on 2012-03-07
> **CharlesA said:**
> upgrade only updates packages and doesn't install new ones. You can use dist-upgrade to install the new packages.
Sorry, I should clarify a little more:
sudo apt-get update & sudo apt-get upgrade leaves packages behind in a "kept back" state.
sudo aptitude update & sudo aptitude upgrade installs everything, even the "kept back" stuff.

---

### Post by snowpine on 2012-03-07
Use:

```
sudo apt-get dist-upgrade
```

to install the held-back upgrades.

(aptitude uses a different syntax.)

---

### Post by teejay17 on 2012-03-07
> **snowpine said:**
> Use:

```
sudo apt-get dist-upgrade
```to install the held-back upgrades.
Is that because there's a new kernel update? I seem to have the "kept back" instance when there's a new kernel. Nonetheless, why would Chromium be part of dist-upgrade?

---

### Post by snowpine on 2012-03-07
> **teejay17 said:**
> Is that because there's a new kernel update? I seem to have the "kept back" instance when there's a new kernel. Nonetheless, why would Chromium be part of dist-upgrade?

I can't really explain it any better than CharlesA did in post #2. Check the man page for more details.

Not a Chromium user so I can't help with that, sorry. :(

---

### Post by jerome1232 on 2012-03-07
If I am understanding correctly, upgrading those packages would require that new packages be installed, apt-get upgrade will not install new packages. You have to use dist-upgrade to allow it to install new packages to complete the upgrade.

---

### Post by snowpine on 2012-03-07
"apt-get upgrade" is equivalent to "aptitude safe-upgrade".

---

### Post by teejay17 on 2012-03-07
Thanks everyone, for the info. It is clearer now. 
The *Coles' Notes* of my understanding is:

[LIST]
[*]Use apt-get updates for an ultra-stable environment, where no packages will be broken by upstream updates.
[/LIST]
[LIST]
[*]Use apt-get dist-upgrade or aptitude update if I want to proceed with the most up-to-date packages.
[/LIST]

---

