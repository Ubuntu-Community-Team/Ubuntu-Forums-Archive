---
title: "How do I prevent an installed deb package from being upgraded?"
date: 2009-11-10
forum: General Help
---

### Post by Rytron on 2009-11-10
Hi.
How do I prevent an installed deb package from being upgraded in Ubuntu?
I refer to Vice 2.1.deb
I know the Synaptic version is also 2.1 but it wont work. I remove .vice from my home folder and completely remove vice in synaptic. 
Then I install Vice 2.1.deb and all works perfectly.

I locked the Vice 2.1.deb vice in Synaptic but when I do update and upgrade it still wants to upgrade vice.

I think the lock feature may only work on native packages. Please someone correct me if I am wrong on that.

Anyone?

---

### Post by nothingspecial on 2009-11-10
Try ```
sudo -s
```

```
echo *[COLOR="Red"]package-name[/COLOR]* hold | dpkg --set-selections
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Kevbert on 2009-11-10
Please take a look at apt_preferences in terminal with
```
man apt_preferences
```
Please post back your results as I've never tried this.
Beaten to it (see post above).

---

### Post by scouser73 on 2009-11-10
> **Rytron said:**
> Hi.
How do I prevent an installed deb package from being upgraded in Ubuntu?
I refer to Vice 2.1.deb
I know the Synaptic version is also 2.1 but it wont work. I remove .vice from my home folder and completely remove vice in synaptic. 
Then I install Vice 2.1.deb and all works perfectly.

I locked the Vice 2.1.deb vice in Synaptic but when I do update and upgrade it still wants to upgrade vice.

I think the lock feature may only work on native packages. Please someone correct me if I am wrong on that.

Anyone?

In **Synaptic Package Manager**, search for the software that you don't want to be upgraded, select it & go to **Package** & then check the box **Lock Version**

---

### Post by Rytron on 2009-11-10
> **scouser73 said:**
> In **Synaptic Package Manager**, search for the software that you don't want to be upgraded, select it & go to **Package** & then check the box **Lock Version**

I tried that. That may only work for native packages.

---

### Post by Rytron on 2009-11-10
> **nothingspecial said:**
> Try ```
sudo -s
```

```
echo *[COLOR="Red"]package-name[/COLOR]* hold | dpkg --set-selections
```

```
sudo apt-get update && sudo apt-get upgrade
```

Excellent nothingspecial. Your solution did the trick.

:popcorn:

---

### Post by alphaniner on 2009-11-10
You shouldn't use **sudo -s** because it retains your user's environment variables.  Use **sudo -i**.

---

### Post by Rytron on 2009-11-10
> **alphaniner said:**
> You shouldn't use **sudo -s** because it retains your user's environment variables.  Use **sudo -i**.

Thanks for the tip alphaniner.

):P

---

### Post by nothingspecial on 2009-11-10
> **alphaniner said:**
> You shouldn't use **sudo -s** because it retains your user's environment variables.  Use **sudo -i**.

Educate me :D

---

