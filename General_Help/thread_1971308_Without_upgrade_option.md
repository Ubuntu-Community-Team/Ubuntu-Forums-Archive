---
title: "Without upgrade option"
date: 2012-05-02
forum: General Help
---

### Post by Jayhawker on 2012-05-02
I was just about to finish 12 04 upgrade from 11 10, but it was being too long and had to cut the process. 
Now I'm trying to upgrade again but when I launch the Update manager, there is no offer to upgrade as it was before the first and frustrated action. 

Please, what I must do to upgrade?

Thank You

---

### Post by bodhi.zazen on 2012-05-02
Interrupting an can sometimes be problematic.

Open a terminal and run:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Any errors ?

---

### Post by Jayhawker on 2012-05-03
> **bodhi.zazen said:**
> Interrupting an can sometimes be problematic.

Open a terminal and run:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Any errors ?

Thanks for your concern. Any error at all. Is 12 04 installed through these orders?

---

### Post by 3rdalbum on 2012-05-03
At what point did you stop the process? Was it downloading the updates, or actually installing them?

If the latter, then a sudo apt-get upgrade should do the trick (as your sources list is already set to 12.04's repository)

If the former, then you need to click the "Upgrade" button next to the words "New release 12.04 LTS is available" in Update Manager. It won't re-download packages that you had already downloaded last time.

---

### Post by Jayhawker on 2012-05-03
Thanks for answering. I'm afraid the process was cut while downloading the updates.

The problem is that the Upgrade button doesn't appear when opening the Update manager. 

any way to solve it?

> **3rdalbum said:**
> At what point did you stop the process? Was it downloading the updates, or actually installing them?

If the latter, then a sudo apt-get upgrade should do the trick (as your sources list is already set to 12.04's repository)

If the former, then you need to click the "Upgrade" button next to the words "New release 12.04 LTS is available" in Update Manager. It won't re-download packages that you had already downloaded last time.

---

